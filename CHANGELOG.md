# Changelog

All notable changes to this project will be documented in this file.

## v1.0.0-beta.3 (2021-06-15)

### Features

- Capture all core-vitals and user experience metrics like FPC, LCP, CLS, User
  timing metrics, etc via chrome tracing [#194](https://github.com/elastic/synthetics/pull/194)
- Split the captured screenshot from each step in to 64 blocks to optimzie
  the storage when indexed the same block in Elaticsearch [#290](https://github.com/elastic/synthetics/pull/290)
- Add support for filtering journeys by name and tags [#300](https://github.com/elastic/synthetics/issues/300)
- Expose `expect` assetion method in the API [#201](https://github.com/elastic/synthetics/issues/201)
- Update Cumulative Layout Shift(CLS) metric based on
  `maximum session window with 1 second gap, capped at 5 seconds`
  [#301](https://github.com/elastic/synthetics/issues/301)
- Expose time taken to complete single step under
  `step.duration.us` [#302](https://github.com/elastic/synthetics/issues/301)
- Expose new capabilities via `--capability` through CLI
  options [#295](https://github.com/elastic/synthetics/issues/295)
- Add new flag `--rich-events` which mimicks heartbeat
  behaviour [#289](https://github.com/elastic/synthetics/pull/289).
- Expose suite parameters from CLI and config file to
  all hooks and journeys callbacks[#272](https://github.com/elastic/synthetics/pull/272)

### Bug fixes

- Move all of the trace events like FCP, LCP, User timings under
  `browser.relative_trace`[#303](https://github.com/elastic/synthetics/pulls/303)
- Prioritize suite params from CLI over config file [#298](https://github.com/elastic/synthetics/pull/298)
- Report errors from `before` and `after` hooks [#273](https://github.com/elastic/synthetics/pull/273)

## v1.0.0-beta.2 (2021-05-17)

### Features

- Allow dynamic suite parameters configuration via `synthetics.config.{js|ts}`
  [#270](https://github.com/elastic/synthetics/issues/270)

### Performance Improvements

- Improve execution time of test suites by spawning journeys in isolated context
  instead of launcing browser for each run [#274](https://github.com/elastic/synthetics/issues/274)

## v1.0.0-beta.1 (2021-05-04)

### Bug fixes

- Exclude all data URI requests from network events [#267](https://github.com/elastic/synthetics/issues/267)

## v1.0.0-beta.0 (2021-04-23)

### Features

- Default to JPEG images with quality 80 for individual step
  screenshots[#233](https://github.com/elastic/synthetics/issues/233)

### Bug fixes

- Keep journey callback types to be synchronous to match with how steps are
  executed synchronously[#256](https://github.com/elastic/synthetics/issues/256)
- Report correct page URL on navigation
  failures[#255](https://github.com/elastic/synthetics/issues/255)

**NOTE: Playwright version is updated to 1.10.0**

## v0.0.1-alpha14 (2021-04-14)

### Features

- Add support for custom reporters for the Synthetics runner
  [#254](https://github.com/elastic/synthetics/issues/254)

## v0.0.1-alpha13 (2021-04-08)

### Features

- Remove duplicate payload fields and keep the network fields under ECS
  [#252](https://github.com/elastic/synthetics/issues/252)

### Bug fixes

- Measure the network timings for aborted and inflight network requests
  correctly[#251](https://github.com/elastic/synthetics/pull/251)

## v0.0.1-alpha12 (2021-03-31)

### Features

- Record transfer size and resource size for all network events
  [#220](https://github.com/elastic/synthetics/issues/220)
- Report the number of journeys as part of the new `synthetics/metadata` event
  which would be used by heartbeat eventually for sharding [#247](https://github.com/elastic/synthetics/pull/247)

## v0.0.1-alpha11 (2021-03-10)

### Features

- Expose driver type information from the agent [#239](https://github.com/elastic/synthetics/pull/239)

Exposing the types allows developers to import the driver type information
directly from the synthetics package instead of using via playwright specific
packages which would result in inconsistent types (version mismatch or
browser specific types).

## v0.0.1-alpha10 (2021-03-04)

### Features

- Move all the ECS specific fields under `root_fields` [#164](https://github.com/elastic/synthetics/issues/164)
- Add support for Junit reporter [#149](https://github.com/elastic/synthetics/issues/149)
- Expose status field for `step/end` and `journey/end` [#230](https://github.com/elastic/synthetics/issues/230)

### Bug fixes

- Disable chromium sandboxing by default
  [#225](https://github.com/elastic/synthetics/issues/225)

## v0.0.1-alpha9 (2021-02-01)

### Features

- Add runtime seccomp profiler for the synthetics agent [#181](https://github.com/elastic/synthetics/issues/181)

### Bug fixes

- Exit with non-zero code when any step/journey fails [#191](https://github.com/elastic/synthetics/issues/191)
- Calculate blocking time properly for missing network data [#187](https://github.com/elastic/synthetics/issues/187)
- Preserve typescript source fails without transpiling to older JS versions [#195](https://github.com/elastic/synthetics/issues/195)
- Capture redirected requests in network timing data [#180](https://github.com/elastic/synthetics/issues/180)
