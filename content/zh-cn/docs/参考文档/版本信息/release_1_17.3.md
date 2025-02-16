---
title: "Release v1.17.3"
linkTitle: "Release v1.17.3"
weight: 1
---

## 下载地址

- [Github Release v1.17.5](https://github.com/polarismesh/polaris/releases/tag/v1.17.5)

## 特性说明

#### 支持 Mesh Sidecar 场景下的单机限流

在 1.17.3 版本中，我们针对 Mesh Sidecar 的场景，支持将 Polaris 的单机限流规则 Spec 通过 Envoy XDS 的格式进行下发给 Sidecar，使得用户在 Mesh 场景下可以享受 Polaris 的限流能力

- 需要搭配 [polaris-controller v1.6.0](https://github.com/polarismesh/polaris-controller/releases/tag/v1.6.0) 版本一起使用

#### 配置中心支持配置回滚、撤回发布

为了让用户有更好的配置中心使用体验，社区在 v1.17.3 版本中支持了配置回滚、撤回某个配置版本发布的能力。当前仅支持通过服务端 OpenAPI 进行操作，前端 UI 支持会在下一个版本中对外放出。

#### 关闭服务端自注册的心跳上报

修改服务端配置

```yaml
bootstrap:
  # Register as Arctic Star Service
  polaris_service:
    # disable_heartbeat disable polaris_server node run heartbeat action to keep lease polaris_service
    disable_heartbeat: true
```

## 版本变化

### 特性

- [[PR 1174]](https://github.com/polarismesh/polaris/pull/1174) feat:support push envoy rls filter xds
- [[PR 1175]](https://github.com/polarismesh/polaris/pull/1175) feat(xds): add OutlierDetection and HealthCheck
- [[PR 1187]](https://github.com/polarismesh/polaris/pull/1187) [Refactor] 配置中心重构+支持配置回滚/撤回发布

### 优化

- [[PR 1162]](https://github.com/polarismesh/polaris/pull/1162) 调整与Eureka实例的状态兼容逻辑
- [[PR 1170]](https://github.com/polarismesh/polaris/pull/1170) refactor:Adjust xds rule build
- [[PR 1179]](https://github.com/polarismesh/polaris/pull/1179) refactor: remove the template code used by map to improve code readability
- [[PR 1202]](https://github.com/polarismesh/polaris/pull/1202) refactor:配置文件缓存逻辑重构

### BUG 修复

- [[PR 1173]](https://github.com/polarismesh/polaris/pull/1173) 单机版为用户关联用户组时，会默认勾选所有用户组
- [[PR 1184]](https://github.com/polarismesh/polaris/pull/1184) 修复通过服务别名拉取时，服务信息为源服务信息问题
- [[PR 1188]](https://github.com/polarismesh/polaris/pull/1188) 用户组token鉴权bug修复；用户名校验规则修改：允许包含英文句号
- [[PR 1192]](https://github.com/polarismesh/polaris/pull/1192) 修复batchConfig批量注销实例配置问题
- [[PR 1196]](https://github.com/polarismesh/polaris/pull/1196) 修复心跳上报写redis异常时未将异常结果返回问题
- [[PR 1208]](https://github.com/polarismesh/polaris/pull/1208) 修复熔断/探测规则更新绑定服务信息后缓存遗留脏数据
- [[PR 1212]](https://github.com/polarismesh/polaris/pull/1212) 修复清理软删除实例时没有同步清理 instance_metadata 以及 health_check 表的数据
- [[PR 1213]](https://github.com/polarismesh/polaris/pull/1214) 修复xDS 生成 cacheKey 时缺失 gatewayService
- [[PR 1201]](https://github.com/polarismesh/polaris/pull/1216) 修复 arm64 环境无法使用 docker image 问题

## New Contributors

* @skywli made their first contribution in https://github.com/polarismesh/polaris/pull/1175
* @qnnn made their first contribution in https://github.com/polarismesh/polaris/pull/1184
* @WTIFS made their first contribution in https://github.com/polarismesh/polaris/pull/1188

**Full Changelog**: https://github.com/polarismesh/polaris/compare/v1.17.2...v1.17.5

## 参与 PolarisMesh 社区

欢迎大家使用体验、Star、Fork、Issue，也欢迎大家参与 PolarisMesh 开源共建！

仓库地址：https://github.com/polarismesh/polaris

项目文档： https://polarismesh.cn/#/

往期发布：https://github.com/polarismesh/polaris/releases