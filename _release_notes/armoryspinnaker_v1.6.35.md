---
layout: post
title: v1.6.35 Armory Enterprise Spinnaker
order: 994
---

# 07/21/17 Release Notes
{:.no_toc}
> Note: If you're experiencing production issues after upgrading Spinnaker, rollback to a [previous working version](http://docs.armory.io/admin-guides/troubleshooting/#i-upgraded-spinnaker-and-it-is-no-longer-responding-how-do-i-rollback).

* This is a placeholder for an unordered list that will be replaced with ToC. To exclude a header, add {:.no_toc} after it.
{:toc}


## Armory Enterprise Spinnaker


### lighthouse - 2296c37
 - Version lock yaml-tools for loading spinnaker configurations
 - use spinnaker configuration ymls to determine whether to use SSL for health checking gate (#72)
 - Notify echo when `/healthcheck` is called (#64)
 - add disk usage to healthcheck (#62)

### dashboard - 2e7c892
 - Do not filter on client. Unsafe. Filter on server.
 - Auto refresh (#15)

## Spinnaker Community Contributions


### orca - v2.14.4
 - fix(pipelinetemplate): Prevent renderer from erasing expressions (#1437)
 - feat(pipelinetemplate): Jinja tag to resolve pipeline ids by app & name (#1432)
 - feat(aws/commits): add build info to execution (#1429)
 - fix(metrics) accidentally used a reserved term in metric tag
 - fix(orca) track task invocations as per v2
 - feat(orca) make v3 the default execution engine
 - feat(metrics) add tags to push and duplicate message metrics (#1431)
 - fix(errors) respect failure status overrides when task throws exception
 - fix(restarts) don't try to prep for restart stages that never started
 - chore(queue): Adding application tag to time all interceptor metrics where possible (#1427)
 - chore(orca): upgrade Kotlin
 - fix(aws): fix monitor task name on delete scaling policy stage (#1404)
 - fix(queue): Correctly wire up priority capacity listener (#1425)
 - fix(aws/deploy): before stage preprocessors were not working on v3
 - feat(queue): Prioritized message capacity guarantees support (#1418)
 - fix(tagging): Fix cleaning of entity tags during rolling push (#1422)
 - fix(pollers): Update TopApplicationExecutionCleanup to scan instead of keys
 - feat(redis/metrics): adds metrics for redis connection pools.
 - feat(task): add flag to let stage succeed on timeout (#1417)
 - fix(queue): rare race condition where branch stops just between other branches stages running
 - fix(pipelinetemplate) make pipelineConfigId optional (#1419)
 - fix(exceptions): ensure exception handlers are evaluated in order
 - chore(orca): more non-null markers
 - chore(orca): mark some nullability constraints for Kotlin's benefit
 - fix(pipelines): remove the generic signature of ExceptionHandler
 - chore(queue): Normalizing traffic shaping metrics (#1412)
 - fix(expressions): fixes an issue with toJson on expressions.
 - fix(queue): ensure null queue state is never returned on new instances
 - fix(queue): retry 429s
 - feat(queue): Redis-backed throttles (#1383)
 - fix(queue): handle recoverable errors when planning a stage
 - chore(queue): marked a bunch of things deprecated that will be removed
 - fix(expressions): should not throw an exception if request was successful (#1408)
 - fix(queue): allow cancellation of paused pipelines
 - chore(expressions): retry within fromUrl expression helper on network errors as well (#1405)
 - fix(clouddriver): NPE safe some HTTP error condition checks
 - fix(permissions): Fix issue creating/deleting application config by updating Permission model (#1395)
 - chore(queue): remove temporary feature flag for message de-duplication
 - chore(queue): tidy up duplication in queue tests
 - fix(queue): temporary flag to control de-duping
 - fix(queue): distinct counter for failing to acquire lock on message read
 - chore(queue): consolidate queue metrics gathering
 - fix(queue): handle old messages that were never hashed
 - fix(queue): clarify callback shenanigans
 - fix(queue): better hash for messages
 - fix(queue): prevent duplicate messages getting pushed to the queue
 - fix(expressions): retry within fromUrl expression helper (#1392)
 - bug fix for https://github.com/spinnaker/spinnaker/issues/1738 (#1398)
 - fix(pipelinetemplate): Handle converting groovy expression syntax better (#1397)
 - chore(queue): improved read lock mechanism
 - fix(pipelinetemplate): Include partials in template merge ops (#1394)
 - chore(build): Conditionally include loadtest project in build (#1376)
 - Avoid NullPointerException by requiring tagsByImageId to be presenent during Find Images by Tags (#1388)
 - fix(orca): don't NPE if a pipeline has `executionEngine:null`
 - fix(queue): don't retry ContinueParentStage if a BEFORE stage has failed
 - feat(provider/dcos): Add support for DC/OS pipelines (#1363)
 - fix(queue): don't ping-pong messages when an execution doesn't exist
 - feat(orca): per-app flag in redis to run orchestrations on v3
 - fix(orca): add a metric for task completions tagged by status and task type
 - fix(orca): stage timeout override can apparently be any type of number
 - fix(orca): safer read of timeout override from stage context
 - fix(orca): honor timeout overrides in v3
 - Additional queue metrics (#1379)
 - fix(orca): restarted pipelines should block new executions
 - fix(orca): fix stall at join stage when branch restarted
 - chore(orca): added a test to ensure optional stage expression edge case works
 - fix(docs): Update PULL_REQUEST_TEMPLATE contributing link (#1375)
 - fix(queue): execution windows should precede parallel stages
 - feat(pipelinetemplate): Support inline templates during plan tasks (#1371)
 - fix(queue): prevent stopped branches from aborting pipelines
 - fix(queue): allow tasks to refer to global context keys seamlessly
 - fix(pipelinetemplate): Remove unused ID property from config schema (#1370)
 - fix(pipelinetemplate): Disallow dots in pipeline template IDs (#1367)

### echo - v1.139.0
 - feat(pipelinetemplate) Add config and type attributes to the trigger payload (#149)
 - fix(rest) - fixes the tokens used for the rest templates (#150)
 - feat(rest): introduces a new configuration option,`insecure` which creates a https client which is insecure by ignoring host verification and does not validate certificate chains. (#148)
 - fix(docs): Update PULL_REQUEST_TEMPLATE contributing link (#147)

### front50 - v1.99.0
 - fix(permissions): Fix issue where not all roles were being synced upon permission modification. (#241)
 - fix(docs): Update PULL_REQUEST_TEMPLATE contributing link (#240)
 - fix(test): Remove account front redis provider to get tests to pass (#238)

### spinnaker - v0.82.0
 - feat(bom): Adds utility to reconstruct source from BOM. (#1745)
 - fix(annotate): Add the human tags to HEAD. (#1748)
 - fix(annotate): Honor manually specified tag override. (#1747)
 - fix(google_images): Supply Halyard with a user to run as. (#1746)
 - fix(install): Supply --user to halyard install script (#1743)
 - fix(validate): fixed location assumptions in tests. (#1741)
 - fix(validate): Fixed server group check in appengine_smoke_test. (#1740)
 - fix(validate): sudo hal deploy apply (#1737)
 - fix(validate): Fixed hal user from previous commit. (#1736)
 - fix(validate): Install halyard with --user (#1735)
 - chore(validate): various validation cleanup and refactoring (#1734)
 - fix(build): Revert change to build numbers. (#1733)
 - feat(validate): Added --halyard_version (#1730)
 - fix(build): Write Halyard version to test into a global file. (#1731)
 - fix(bom): Quick fix for Debian repo URI. (#1727)
 - fix(bom): Make git artifact source name agnostic. (#1726)
 - fix(build): Write build subprocess output to file. (#1719)
 - feat(bom): Adds artifact sources so BOM is self-describing. (#1715)
 - feat(bom): Include component commit hashes in BOM. (#1720)
 - fix(validate): Fix validating aws deployments (#1718)
 - fix(publish): Change to UTC time and clean git artifacts. (#1716)
 - feat(validate): validate halyard aws. (#1714)
 - chore(install): Halyard bootscript (#1486)
 - feat(halyard): Build halyard image (#1709)
 - fix(publish_bom): Can't cat strings to lists. (#1712)
 - fix(build): Include all subsystems in index. (#1710)
 - fix(build): Space out container builds. (#1707)
 - Create README.md
 - Update README.md
 - feat(halyard): Base install for c2d (#1706)
 - fix(dev): various fixes to build scripts (#1700)
 - Pin redis version on first boot (#1704)
 - Updates PR template contributing URL (#1702)
 - fix(changelog_gist): Don't chop off first component name. (#1701)
 - fix(component_image): Can't gcloud get instances (#1699)
 - fix(changelog): Sanitize changelog and rename changelog post. (#1697)
 - Config network protocol used (#1693)
 - fix(validate): Fixed front50 test (#1694)
 - feat(validation): Monitor validation (#1691)
 - feat(validate): Deploy to EC2 (#1688)
 - fix(bake): Warn when quota may be exhausted (#1689)
 - fix(publish/halyard): Ensure docs are always unique (#1687)
 - fix(validate): pass through hal_user when ssh/scp (#1685)
 - fix(bake): Allow auto-delete flag to propagate (#1686)
 - fix(validate): Handle no-argument flags (#1682)
 - fix(deploy): publish stable halyard version (#1681)
 - fix(publish_changelog): Don't use full path name for 'created by' file (#1679)
 - fix(google_kato_test): Temporarily remove list image test. (#1680)
 - feat(validate): Run appengine integration tests. (#1676)

### deck - v2.1126.0
 - fix(gce): prevent npe when loading server group wizard in project without default network (#3863)
 - fix(provider/amazon): Fix deleting ALBs (#3862)
 - chore: bump core to 0.0.26 and amazon to 0.0.10 (#3861)
 - feat(provider/amazon): Cleanup ALB listeners CRUD UI (#3857)
 - feat(pipeline/RunJob): Allow container name conf (#3858)
 - fix(core): reduce badge size in compact headers (#3855)
 - feat(provider/google): Add support for Minimum CPU Platform. (#3856)
 - feat(core): require app name in appModelBuilder.createApplication (#3850)
 - feat(gce): better custom instance selector (#3851)
 - fix(gce): minor formatting change for user data input field (#3829)
 - fix(provider/gce): Make the linter happy. (#3854)
 - Revert "feat(provider/google): Add ILB listeners." (#3853)
 - fix(provider/amazon): Fix missing information for ALB target groups (#3852)
 - fix(aws): change "deprecated" to "not recommended" on rolling push (#3849)
 - fix(aws): provide explanatory text when no target groups present (#3847)
 - fix(core/entityTag): Clone more fields in UI when editing an entity tag (#3848)
 - fix(core) dedupe execution account labels (#3845)
 - fix(gce): placate linter (#3844)
 - fix(permissions): Prevent user from only specifying READ permission, and thus locking everyone out of that application (#3835)
 - chore(canary): move canary out of core to separate module (#3843)
 - fix(core): import from base rxjs (#3842)
 - chore(core): bump to 0.0.22 (#3841)
 - fix(gce): cast load balancers to pacify TS compiler (#3840)
 - chore(core): bump package to 0.0.21 (#3839)
 - fix(core): correctly set default state on custom strategy params (#3836)
 - feat(core/entityTag): optionally render titles on alerts
 - fix(core/entityTag): delete unused code
 - feat(core/entityTag): Tweak alert category descriptions (again)
 - feat(provider/google): Add ILB listeners. (#3832)
 - feat(core/entityTag): Wait 100ms before showing entity tag popover
 - feat(provider/google): Add support for Shared VPC Networking (XPN). (#3831)
 - feat(core/entityTag): Tweak alert category descriptions (#3830)
 - fix(core/executions): Show durations in execution details/permalink (#3809)
 - feat(provider/kubernetes): Run Job extended config (#3823)
 - feat(core): move canary/aca to core, remove netflix references
 - feat(core): restore canary/aca stages
 - feat(kubernetes) instance links (#3827)
 - chore(provider/google): Update auth scopes tooltip. (#3826)
 - fix(core): include "feature" on spinnaker component ctrl
 - fix(aws): restrict rolling push strategy to AWS
 - fix(pipelines): fix float on health counts
 - refactor(provider/amazon): Convert createClassicLoadBalancer to TS and extract common functions (#3818)
 - fix(pipeline-template): follow angular module name conventions for pipeline template plan errors component
 - fix(pipeline-templates) fix rendering issues for errors and help fields (#3819)
 - refactor(aws): make scaling policies customizable
 - fix(provider/amazon): Require target groups to have unique names
 - refactor(provider/amazon): convert createApplicationLoadBalancer to TS (#3816)
 - Bug fix where preconfigured webhook is not sending HTTP headers
 - fix(kubernetes): Search not working if result contained K8S load balancer
 - fix(provider/amazon): Fix key collisions when an ALB and classic LB existed with the same name
 - fix(provider/amazon): Fix instance health setting in target groups (#3813)
 - refactor(provider/amazon): Separate load balancer types (#3810)
 - feat(core): include description in applications list view
 - refactor(provider/amazon): Convert load balancer transformer to TS (#3806)
 - fix(tests): exclude /lib/ from test context
 - feat(provider/amazon): CRUD for ALBs (#3803)
 - feat(google): adds ability to package deck/google as a library (#3805)
 - feat(provider/kubenretes): Support downward API env vars (#3804)
 - feat(core): automatically scroll to server group on deep link
 - fix(pipelines): correct diff on stages, smaller stringVal, dedupes
 - chore(docker): rev package to 0.0.17
 - chore(core) rev package to 0.0.17
 - fix(core): initialize strategy selector
 - feat(provider/amazon): Add link back to load balancer from target group details (#3796)
 - feat(provider/amazon): Expose ipAddressType in the ALB details panel (#3795)
 - fix(provider/amazon): Add server groups to target group details (#3794)
 - fix(core/bootstrap): Add missing imports
 - feat(bake/docker) add rebake flag to docker bakes (#3792)
 - refactor(core): Rename core.module to typescript - Remove uirouter.stateEvents.shim.js - Refactor app initialization blocks to separate files
 - fix(provider/amazon): fix load balancer vpc id
 - fix(provider/gce): Disallow editing ports for ILBs. (#3790)
 - chore(core): Update core/tsconfig.json to include all typescript files
 - feat(pipeline-templates): config view (#3787)
 - chore(core): Update to @uirouter/angularjs@1.0.3
 - fix(firefox): Fix application config scrolling in firefox (#3785)
 - chore(core): Bump version to 0.0.16
 - fix(Markdown): Do not render when `message` is empty
 - chore(core): Bump version to 0.0.15 (#3783)
 - chore(provider/amazon): Bump amazon to 0.0.6 (#3782)
 - fix(docs): Update PULL_REQUEST_TEMPLATE contributing link (#3781)
 - the static html in /opt/deck/html is not generated when building an RPM because the dependency is not set in build.gradle. Fixing it.
 - feat(core/entityTag): Render tagline for alerts, if present (#3779)
 - feat(core/entityTag): Add categories to alerts popovers (#3773)
 - chore(expression-docs): change expression docs link (#3778)
 - chore(core): rev version to 0.0.14
 - feat(core): Common ratelimit http header (#3775)
 - refactor(provider/amazon): Convert serverGroupConfiguration.service to TS (#3774)
 - fix(provider/kubernetes): fixes bug with edit server group dialog delays (#3719)
 - refactor(strategies): make strategies provider-pluggable, convert to TS
 - refactor(provider/amazon): Convert serverGroup.transformer to TS and type ScalingPolicies (#3770)
 - fix(provider/amazon): Add originl refresh time back to load balancer selector
 - refactor(provider/amazon): Convert load balancer selector to TS
 - chore(amazon): ensure module names all start with "spinnaker.amazon"
 - feat(core): include help on instance port, align checkboxes
 - fix(entityTags): do not pre-optimize tag retrieval in data source

### gate - v3.44.0
 - feat(provider/amazon): Provide endpoints for the certificate provider in clouddriver (#414)
 - fix(insight-links): filter invalid insight links based on cloud provider (#412)
 - feat(applications): allow filtering on accounts from /applications endpoint (#409)
 - fix(ratelimit): Check user for anonymous email (#408)
 - fix(web): Implementing missed clouddriver selector callsites (#407)
 - fix(api-docs): Pull in new swagger library & include Auth controller in generated docs (#406)
 - feat(web): Request-time clouddriver client selection (#405)
 - feat(*): Set anonymous principal to x-ratelimit-app header if provided (#404)
 - fix(ratelimit): Correctly log principal name (#403)
 - fix(docs): Update PULL_REQUEST_TEMPLATE contributing link (#401)
 - feat(ratelimit): Adding principal metrics (#402)
 - fix(web): Include better context in save pipeline template ops (#400)
 - fix(ratelimit): Ignore deck API requests (#399)

### rosco - v0.97.0
 - feat(google/xpn): Add support for shared VPC networks. (#212)
 - Add Ubuntu 14.04 ami for us-east-2 (#211)
 - Having the -e in the shebang generates a POSTIN scriplet error during installation. (#209)
 - chore(config): Switch to non-deprecated config & remove 12.04 from gce images (#204)
 - fix(core): Explicitly convert -var-file GString to String to avoid CCE on json serialization to redis. (#207)
 - fix(docs): Update PULL_REQUEST_TEMPLATE contributing link (#206)
 - feat(core): Add hostname to roscoInstanceId (#205)
 - chore(halconfig): configDir should be static (#203)

### clouddriver - v1.649.0
 - fix(aws/updateLaunchConfig): update block devices when changing instance types
 - fix(provider/kubernetes): Update HPA endpoint for k8s 1.6 (#1692)
 - feat(kubernetes): cache additional resources (#1719)
 - fix(aws/serverGroup): add build info (#1718)
 - feat(provider/dcos): Add deploy and clone server group operations (#1703)
 - fix(amazon): handle instance not found exception in describeinstances (#1715)
 - fix(provider/amazon): Allow target groups to have more than one lsitener (#1713)
 - feat(provider/kubernetes): Configure Service Acct (#1711)
 - fix(provider/amazon): Check default actions for used target group names (#1712)
 - fix(amazon): send correct source region when copying scaling policies (#1704)
 - fix(provider/amazon): Fix create alb for real (#1709)
 - fix(provider/amazon): fix the alb create validator (#1707)
 - feat(provider/amazon): Support on demand caching for ALBs (#1689)
 - fix(provider/amazon): Certificate provider is optional (#1706)
 - feat(provider/amazon): Add cachingagent and provider for server certificates (#1702)
 - fix(provider/amazon): Fix deleting of classic load balancers (#1705)
 - fix: allow k8s configMaps to have no items (#1701)
 - feat(provider/google): Add support for Minimum CPU Platform. (#1699)
 - fix(provider/google): Handle empty xpn resources. (#1698)
 - feat(provider/dcos): Load balancer and secret caching agents (#1696)
 - fix(cats): Remove lock key from Redis when agent is unscheduled. (#1695)
 - chore(core): Update spinnaker-dependencies version. (#1697)
 - feat(provider/google): Support multiple listeners for ILBs. (#1693)
 - feat(provider/amazon): Add validation rules around listeners and target groups (#1694)
 - feat(provider/google): Add support for Shared VPC Networking (XPN). (#1691)
 - fix(requestQueue): differentiate timeout in queue vs in processing.
 - feat(provider/dcos): Server group and instance caching agents (#1674)
 - feat(provider/amazon): Remove associated listeners and target groups on delete of ALB (#1687)
 - feat(provider/kubernetes): Annotation config (#1686)
 - fix(appengine): prevent flaky appengine deploy failures (#1685)
 - feat(provider/oraclebmcs): Adding initial loadbalancer support (#1673)
 - Sanitize logging in clouddriver (#1530)
 - feat(provider/kubernetes): Run Job Pod Labels (#1683)
 - fix(provider/google): Respect pagination tokens when querying aggregated machine types on startup. (#1682)
 - feat(provider/amazon): Use edda if available for listener rules (#1680)
 - feat(provider/amazon): Use ActionTypeEnum value everywhere to make alb upsert simpler (#1681)
 - fix(provider/kubernetes): Field refs were not loaded (#1678)
 - feat(provider/amazon): Support caching of Rules and support CRUD of rules (#1675)
 - fix(requestqueue): adds additional instrumentation.
 - fix(provider/google): Don't NPE when machine types aren't returned. (#1672)
 - fix(provider/amazon): NullPointerException if Edda is not present (#1671)
 - fix(loadtest): Simplified load configuration (#1670)
 - fix(loadtest): Adjust logging configuration (#1669)
 - feat(provider/dcos): Add initial scaffolding for DC/OS provider (#1636)
 - feat(provider/amazon): Add support to upsert an ALB with certs on the listener (#1664)
 - feat(provider/amazon): Use edda views if available for TargetGroup* and Listener aching (#1662)
 - feat(request buffer): optional buffer to distribute api requests
 - fix(provider/amazon): Disable alb caching via edda by default (#1668)
 - feat(loadtest): Rough cut of some gatling-based load tests for clouddriver (#1666)
 - change instance lookup for enable/disable to not issue a describeInstances with a filter but instead ask for known instance ids
 - fix(provider/amazon): Fix ELB deploy; stop modifying the input (#1665)
 - feat(provider/amazon): Add target groups to load balancer description on direct lookup (#1663)
 - fix(provider/amazon): add gov-cloud special case to arn patterns (#1653)
 - fix(provider/google): Wait for L4 LB instance deregister. (#1658)
 - refactor(provider/amazon): normalize elbv2 names (#1657)
 - fix(provider/amazon): Fix load balancer loading (#1660)
 - fix(docs): Update PULL_REQUEST_TEMPLATE contributing link (#1656)
 - fix(provider/amazon): Fix upsert ALB when target group does not exist (#1655)
 - feat(provider/amazon): Add target group lists to load balancer summary (#1651)
 - fix(eureka): Add back eureka caching agent (#1654)
