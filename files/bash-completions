# $FreeBSD$
#
_pkgs_list() {
	local dbdir="$1"
	shift 1 # the rest will be passed diretly to compgen
	if TMPDIR=/dev/null ASSUME_ALWAYS_YES=1 \
	    PACKAGESITE=file:///nonexistent \
	    pkg info -x 'pkg(-devel)?$' >/dev/null 2>&1; then
		compgen -W "$(pkg info -aq)" $*
	else
		cd ${dbdir} && compgen -d $*
	fi
}

_portmaster () {
	local cur dbdir portsdir
	cur=${COMP_WORDS[COMP_CWORD]}
	dbdir=${PKG_DBDIR:-/var/db/pkg}
	portsdir=${PORTSDIR:-/usr/ports}

	case "$cur" in
	${portsdir}/*)
		COMPREPLY=( $( compgen -d $cur ) ) ;;
	*/*)	COMPREPLY=( $( compgen -d ${portsdir}/$cur ) ) ;;
	--*)	COMPREPLY=( $( compgen -W '--force-config --show-work \
		--packages --packages-only \
		--packages-build --packages-if-newer --delete-build-only \
		--always-fetch --delete-packages \
		--local-packagedir= --packages-local \
		--update-if-newer \
		--no-confirm --no-term-title --no-index-fetch \
		--index --index-first --index-only \
		--clean-distfiles --clean-packages \
		--check-depends --check-port-dbdir --list-origins \
		--help --version' -- $cur ) )
		;;
	*)	COMPREPLY=( $(_pkgs_list ${dbdir} "${cur}" ) )
		COMPREPLY=( ${COMPREPLY[@]#${dbdir}/} )
		COMPREPLY=( ${COMPREPLY[@]} $( compgen -d ${portsdir}/$cur ) )
		COMPREPLY=( ${COMPREPLY[@]#/ports/} )
		;;
	esac

	return 0
}
complete -F _portmaster portmaster
