matrixJob('Periodic go-systemd builder from dsl') {
    scm {
        git {'https://github.com/coreos/go-systemd.git', '*/master'}
    }

    concurrentBuild()

    triggers {
        cron('@daily')
    }

    axes {
        label('debian-testing', 'fedora-24', 'fedora-25')
        axis {
            name('os_type')
        }
    }

    wrappers {
        buildName('go-systemd master (periodic #${BUILD_NUMBER})')
        timeout {
            absolute(25)
        }
    }

    steps {
        shell('./scripts/jenkins/go-systemd-master.sh')
    }
}
