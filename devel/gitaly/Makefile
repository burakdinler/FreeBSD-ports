# $FreeBSD$

PORTNAME=	gitaly
DISTVERSION=	13.4.2
PORTREVISION=	0
CATEGORIES=	devel

MAINTAINER=	mfechner@FreeBSD.org
COMMENT=	Smart reverse proxy for GitLab

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

# define dependencies that are required for build and run under MY_DEPENDS
MY_DEPENDS=	git>=2.28:devel/git \
		rubygem-bundler>=1.17.3:sysutils/rubygem-bundler \
		rubygem-rugged>=0.28:devel/rubygem-rugged \
		rubygem-github-linguist>=7.9<8.0:textproc/rubygem-github-linguist \
		rubygem-gitlab-markup>=1.7.1<1.8.0:textproc/rubygem-gitlab-markup \
		rubygem-activesupport60>=6.0.3.1<6.0.4:devel/rubygem-activesupport60 \
		rubygem-rdoc>=6.1<7.0:devel/rubygem-rdoc \
		rubygem-gitlab-gollum-lib>=4.2.7.9<4.2.8:www/rubygem-gitlab-gollum-lib \
		rubygem-gitlab-gollum-rugged_adapter>=0.4.4.2<0.4.5.0:www/rubygem-gitlab-gollum-rugged_adapter \
		rubygem-grpc124>=1.24.0:net/rubygem-grpc124 \
		rubygem-sentry-raven>=3.0<4:devel/rubygem-sentry-raven \
		rubygem-faraday>=1.0.1<2:www/rubygem-faraday \
		rubygem-rbtrace>=0.4.14:devel/rubygem-rbtrace \
		rubygem-gitlab-labkit>=0.12.1<0.13:devel/rubygem-gitlab-labkit \
		rubygem-licensee8>=8.9.0<8.10.0:devel/rubygem-licensee8 \
		rubygem-google-protobuf38>=3.8.0<3.9.0:devel/rubygem-google-protobuf38
BUILD_DEPENDS=	gem:devel/ruby-gems \
		bash>0:shells/bash \
		${MY_DEPENDS}
RUN_DEPENDS=	${MY_DEPENDS} \
		gitlab-shell>=9.3.0:devel/gitlab-shell
LIB_DEPENDS=	libgit2.so:devel/libgit2

USES=		gmake go:modules,no_targets pkgconfig
USE_RUBY=	yes

MAKE_ENV=	GOFLAGS="${GO_BUILDFLAGS}"

USE_GITLAB=	yes
GL_ACCOUNT=	gitlab-org
# Find this here: https://gitlab.com/gitlab-org/gitaly/-/tags
GL_COMMIT=	60a08d8121b1019ee7868a9d8e22e6f3d98233ad

# for go dependencies
USE_GITHUB=	nodefault
# generated with: make gomod-vendor
# 55dd
GH_TUPLE=	\
		BurntSushi:toml:v0.3.1:burntsushi_toml/vendor/github.com/BurntSushi/toml \
		DataDog:dd-trace-go:v1.7.0:datadog_dd_trace_go/vendor/gopkg.in/DataDog/dd-trace-go.v1 \
		beorn7:perks:v1.0.1:beorn7_perks/vendor/github.com/beorn7/perks \
		census-instrumentation:opencensus-go:v0.22.2:census_instrumentation_opencensus_go/vendor/go.opencensus.io \
		client9:reopen:v1.0.0:client9_reopen/vendor/github.com/client9/reopen \
		cloudflare:tableflip:4baec9811f2b:cloudflare_tableflip/vendor/github.com/cloudflare/tableflip \
		codahale:hdrhistogram:3a0bb77429bd:codahale_hdrhistogram/vendor/github.com/codahale/hdrhistogram \
		davecgh:go-spew:v1.1.1:davecgh_go_spew/vendor/github.com/davecgh/go-spew \
		getsentry:sentry-go:v0.5.1:getsentry_sentry_go/vendor/github.com/getsentry/sentry-go \
		go-gorp:gorp:v1.7.2:go_gorp_gorp/vendor/gopkg.in/gorp.v1 \
		go-yaml:yaml:v2.2.8:go_yaml_yaml/vendor/gopkg.in/yaml.v2 \
		golang:appengine:v1.6.5:golang_appengine/vendor/google.golang.org/appengine \
		golang:groupcache:215e87163ea7:golang_groupcache/vendor/github.com/golang/groupcache \
		golang:net:6afb5195e5aa:golang_net/vendor/golang.org/x/net \
		golang:oauth2:bf48bf16ab8d:golang_oauth2/vendor/golang.org/x/oauth2 \
		golang:protobuf:v1.3.2:golang_protobuf/vendor/github.com/golang/protobuf \
		golang:sync:cd5d95a43a6e:golang_sync/vendor/golang.org/x/sync \
		golang:sys:86b910548bc1:golang_sys/vendor/golang.org/x/sys \
		golang:text:v0.3.3:golang_text/vendor/golang.org/x/text \
		google:go-genproto:ca5a22157cba:google_go_genproto/vendor/google.golang.org/genproto \
		google:pprof:d4f498aebedc:google_pprof/vendor/github.com/google/pprof \
		google:uuid:v1.1.1:google_uuid/vendor/github.com/google/uuid \
		googleapis:gax-go:v2.0.5:googleapis_gax_go_v2/vendor/github.com/googleapis/gax-go \
		googleapis:google-api-go-client:v0.15.0:googleapis_google_api_go_client/vendor/google.golang.org/api \
		googleapis:google-cloud-go:v0.50.0:googleapis_google_cloud_go/vendor/cloud.google.com/go \
		grpc-ecosystem:go-grpc-middleware:v1.0.0:grpc_ecosystem_go_grpc_middleware/vendor/github.com/grpc-ecosystem/go-grpc-middleware \
		grpc-ecosystem:go-grpc-prometheus:v1.2.0:grpc_ecosystem_go_grpc_prometheus/vendor/github.com/grpc-ecosystem/go-grpc-prometheus \
		grpc:grpc-go:v1.24.0:grpc_grpc_go/vendor/google.golang.org/grpc \
		kelseyhightower:envconfig:v1.3.0:kelseyhightower_envconfig/vendor/github.com/kelseyhightower/envconfig \
		konsorten:go-windows-terminal-sequences:v1.0.2:konsorten_go_windows_terminal_sequences/vendor/github.com/konsorten/go-windows-terminal-sequences \
		lib:pq:v1.2.0:lib_pq/vendor/github.com/lib/pq \
		libgit2:git2go:v30.0.5:libgit2_git2go_v30/vendor/github.com/libgit2/git2go/v30 \
		lightstep:lightstep-tracer-go:v0.15.6:lightstep_lightstep_tracer_go/vendor/github.com/lightstep/lightstep-tracer-go \
		mattn:go-runewidth:v0.0.4:mattn_go_runewidth/vendor/github.com/mattn/go-runewidth \
		matttproud:golang_protobuf_extensions:v1.0.1:matttproud_golang_protobuf_extensions/vendor/github.com/matttproud/golang_protobuf_extensions \
		olekukonko:tablewriter:v0.0.2:olekukonko_tablewriter/vendor/github.com/olekukonko/tablewriter \
		opentracing:opentracing-go:v1.0.2:opentracing_opentracing_go/vendor/github.com/opentracing/opentracing-go \
		philhofer:fwd:v1.0.0:philhofer_fwd/vendor/github.com/philhofer/fwd \
		pkg:errors:v0.8.1:pkg_errors/vendor/github.com/pkg/errors \
		pmezard:go-difflib:v1.0.0:pmezard_go_difflib/vendor/github.com/pmezard/go-difflib \
		prometheus:client_golang:v1.0.0:prometheus_client_golang/vendor/github.com/prometheus/client_golang \
		prometheus:client_model:14fe0d1b01d4:prometheus_client_model/vendor/github.com/prometheus/client_model \
		prometheus:common:v0.4.1:prometheus_common/vendor/github.com/prometheus/common \
		prometheus:procfs:v0.0.3:prometheus_procfs/vendor/github.com/prometheus/procfs \
		rubenv:sql-migrate:06338513c237:rubenv_sql_migrate/vendor/github.com/rubenv/sql-migrate \
		sebest:xff:6c115e0ffa35:sebest_xff/vendor/github.com/sebest/xff \
		sirupsen:logrus:v1.4.2:sirupsen_logrus/vendor/github.com/sirupsen/logrus \
		stretchr:testify:v1.4.0:stretchr_testify/vendor/github.com/stretchr/testify \
		tinylib:msgp:v1.1.0:tinylib_msgp/vendor/github.com/tinylib/msgp \
		uber:jaeger-client-go:v2.15.0:uber_jaeger_client_go/vendor/github.com/uber/jaeger-client-go \
		uber:jaeger-lib:v1.5.0:uber_jaeger_lib/vendor/github.com/uber/jaeger-lib

GL_TUPLE=	gitlab-org:gitlab-shell:82ec8144fb2a04d78f29ae5d1f4e5a407257309f:gitlab_org_gitlab_shell/vendor/gitlab.com/gitlab-org/gitlab-shell \
		gitlab-org:labkit:45895e1290291a2519678a847a24edb22880b9e6:gitlab_org_labkit/vendor/gitlab.com/gitlab-org/labkit

post-patch:
	${REINPLACE_CMD} -e "s|%%PREFIX%%|${PREFIX}|" ${WRKSRC}/config.toml.example
	${REINPLACE_CMD} -e "s|%%PREFIX%%|${PREFIX}|" ${WRKSRC}/ruby/gitlab-shell/config.yml.example
	${MV} ${WRKSRC}/config.toml.example ${WRKSRC}/config.toml.sample
	${MV} ${WRKSRC}/ruby/gitlab-shell/config.yml.example ${WRKSRC}/ruby/gitlab-shell/config.yml.sample

do-install:
	${MKDIR} ${STAGEDIR}${DATADIR}
	${MKDIR} ${STAGEDIR}${DATADIR}/bin
	${FIND} ${WRKSRC} -name '*.orig' -delete
	${FIND} ${WRKSRC} -name "Gemfile.lock" -delete
	(cd ${WRKSRC}/_build/bin/ && ${COPYTREE_SHARE} .  ${STAGEDIR}${DATADIR}/bin && \
	cd ${WRKSRC} && ${COPYTREE_SHARE} config.toml.sample  ${STAGEDIR}${DATADIR}) && \
	cd ${WRKSRC}/ruby && ${COPYTREE_SHARE} . ${STAGEDIR}${DATADIR}/ruby

.include <bsd.port.mk>
