# 浩瀚世界 Vast Worlds

面向 Minecraft Java Edition 1.21.1 的世界生成数据包（非模组，无需 Fabric/Forge/TerraBlender）。在保留原版主世界生成的基础上，新增 3 个自定义生物群系。

## 版本信息

- 当前版本：1.0.0
- 游戏版本：Minecraft Java Edition 1.21.1
- 数据包格式：48
- 类型：世界生成数据包

## 生物群系

| ID | 中文名 | 特征 |
| --- | --- | --- |
| `vastworlds:mega_plains` | 巨型平原 | 温和气候、连绵起伏的开阔草原，生成羊、牛、马、兔子 |
| `vastworlds:towering_hills` | 高耸丘陵 | 寒冷干燥、低侵蚀的高海拔山地，生成山羊 |
| `vastworlds:deep_valley` | 深谷 | 温暖湿润、靠近海岸的陡峭山谷，生成常见农场动物 |

## 实现方式

- 覆盖 `data/minecraft/dimension/overworld.json`
- 保留原版主世界的 827 条生物群系参数，追加 4 条自定义参数点
- 地形仍使用原版 `minecraft:overworld` 噪声设置，因此地形高度与结构保持原版
- 生物群系定义位于 `data/vastworlds/worldgen/biome/`
- 通过 `#minecraft:is_overworld` 标签将自定义群系纳入主世界

## 安装

1. 从 Releases 下载 `vastworlds-datapack-1.0.0.zip`
2. 放入 `saves/<世界名>/datapacks/`；服务器放入 `<世界目录>/datapacks/`
3. 新建世界，或进入世界后执行 `/reload`，并前往尚未生成的区域
4. 使用 `/locate biome vastworlds:mega_plains`（或 `towering_hills`、`deep_valley`）查找群系

## 重新打包

```bash
cd vastworlds-datapack
zip -r ../vastworlds-datapack-1.0.0.zip .
```

## 已知限制

- 只影响新生成的区块，已有区块不会改变
- 纯数据包无法完全复现原 TerraBlender 的权重共存机制，群系位置由气候参数竞争决定
- `misty_cascade_gorge` 未包含：原实现引用了不存在的类，且没有对应的生物群系 JSON
- 原模组源码仍保留在 `src/`，本数据包不依赖它，也无需构建

## 许可

MIT
