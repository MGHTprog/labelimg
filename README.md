# labelImg 正反馈版

一个基于 Python + Qt 的桌面图像标注工具，支持为目标绘制矩形框，并将标注保存为常见的目标检测格式。

本项目基于 [labelImg](https://github.com/HumanSignal/labelImg) v1.8.6，针对连续标注场景增加了更清晰的操作反馈。

## 主要改进

- 状态栏显示绿色动态进度条：当前图片、总图片数和完成百分比。
- 切换图片时进度条平滑更新，方便掌握数据集标注进度。
- 新增标注、保存成功后显示即时确认提示。
- 到达目录中的最后一张图片时显示完成提示。
- 标注框线宽调整为约 4 像素，在复杂图片和缩放场景下更醒目。

## 支持的标注格式

- Pascal VOC：XML
- YOLO：TXT
- CreateML：JSON

## 环境要求

- Python 3
- PyQt5
- Windows、Linux 或 macOS

## 安装与运行

### 从源码运行

```bash
git clone https://github.com/MGHTprog/labelimg.git
cd labelimg
python -m pip install -r requirements/requirements-linux-python3.txt
python labelImg.py
```

Windows 用户如果已经安装 PyQt5，也可以直接运行：

```powershell
python labelImg.py
```

如果需要预置类别文件：

```bash
python labelImg.py path/to/images data/predefined_classes.txt
```

首次从源码运行前，如果缺少 Qt 资源文件，可执行：

```bash
pyrcc5 -o libs/resources.py resources.qrc
```

## 基本使用

1. 点击 **Open Dir** 选择图片目录。
2. 点击 **Create RectBox**，在图片上拖动鼠标创建标注框。
3. 输入类别名称并确认。
4. 点击 **Save** 保存当前图片标注。
5. 使用工具栏或快捷键切换上一张/下一张图片。
6. 观察状态栏进度条，了解当前数据集处理进度。

常用快捷键：

| 快捷键 | 功能 |
| --- | --- |
| `Ctrl+O` | 打开图片 |
| `Ctrl+U` | 打开图片目录 |
| `Ctrl+S` | 保存标注 |
| `W` | 创建矩形框 |
| `D` | 下一张图片 |
| `A` | 上一张图片 |
| `Del` | 删除选中的标注框 |

## 项目结构

```text
labelimg/
├── labelImg.py       # 主窗口和交互逻辑
├── libs/              # 画布、图形、格式读写等模块
├── data/              # 预置类别和应用数据
├── resources/         # 图标及 Qt 资源
├── demo/              # 示例图片
└── tests/             # 测试代码
```

## 开发说明

语法检查：

```bash
python -m py_compile labelImg.py libs/shape.py
```

标注框线宽在 `libs/shape.py` 中统一控制；状态栏进度反馈和操作提示在 `labelImg.py` 中实现。

## 许可证

本项目沿用原 labelImg 项目的 MIT License，详见 [LICENSE](LICENSE)。

## 致谢

感谢原 labelImg 项目及其贡献者。本仓库专注于改善连续标注时的可见反馈和操作体验。
