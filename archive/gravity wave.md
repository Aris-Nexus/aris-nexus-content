---
title: visualization test
date: 2026-03-21T16:07:04.241Z
---

Test::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
<PythonViz 
  packages={["numpy", "matplotlib"]}
  interactive={true}
  params={[{"name":"freq","label":"frequency","desc":"控制涟漪的密集程度","min":1,"max":10,"val":3.2},{"name":"amp","label":"amplitude","desc":"","min":0.1,"max":3,"val":1.5},{"name":"decay","label":"","desc":"","min":0,"max":0.5,"val":0.1}]}
  code={`# 3D 量子引力波纹演示
import numpy as np
import matplotlib
matplotlib.use("Agg")
import matplotlib.pyplot as plt
import io, base64

# 1. 构建 3D 空间网格
x = np.linspace(-10, 10, 80)
y = np.linspace(-10, 10, 80)
X, Y = np.meshgrid(x, y)

# 计算网格上每个点到中心的距离 R
R = np.sqrt(X**2 + Y**2)

# 2. 核心数学模型：带衰减的 3D 涟漪方程
# 直接使用系统注入的滑条变量：amp(振幅), freq(频率), decay(衰减)
Z = amp * np.sin(freq * R) * np.exp(-decay * R)

# 3. 赛博朋克视觉渲染
plt.style.use("dark_background")
fig = plt.figure(figsize=(8, 6), facecolor="#09090b")
ax = fig.add_subplot(111, projection="3d")
ax.set_facecolor("#09090b")

# 使用黑底+翡翠绿网格线，打造极致的极客扫描感
ax.plot_surface(X, Y, Z, color='#000000', edgecolor='#10b981', lw=0.6, alpha=0.9)

# 固定 Z 轴的高度比例，防止形变
ax.set_zlim(-3, 3)
ax.view_init(elev=40, azim=45)
ax.axis("off")

# 4. 内存转储与 Base64 编码
buf = io.BytesIO()
plt.savefig(buf, format="png", dpi=120, bbox_inches="tight")
plt.close(fig)
buf.seek(0)
img_str = base64.b64encode(buf.read()).decode("utf-8")

# 返回给 React 前端
f"data:image/png;base64,{img_str}"`} 
/>
FIRST TEST

<PythonViz 
  packages={["numpy", "matplotlib"]}
  interactive={true}
  params={[{"name":"pulse","label":"频率","desc":"控制主波形的震荡频率","min":0.5,"max":5,"val":4.7},{"name":"noise","label":"噪声","desc":"模拟环境随机信号的强度","min":0,"max":1,"val":1},{"name":"bias","label":"偏移","desc":"调整波形的垂直中心偏移","min":-2,"max":2,"val":0.7}]}
  code={`# 2D 生物节律频谱分析
import numpy as np
import matplotlib
matplotlib.use("Agg")
import matplotlib.pyplot as plt
import io, base64

# 1. 生成时间轴数据
t = np.linspace(0, 10, 500)

# 2. 构建数学模型
# 使用注入变量：pulse (频率), noise (噪声强度), bias (基准)
# 模拟主信号 + 随机干扰
base_signal = np.sin(pulse * t) + bias
random_noise = np.random.normal(0, noise, t.shape)
final_signal = base_signal + random_noise

# 3. 2D 赛博风格渲染
plt.style.use("dark_background")
fig, ax = plt.subplots(figsize=(8, 4), facecolor="#09090b")
ax.set_facecolor("#09090b")

# 绘制主曲线 (Emerald 500)
ax.plot(t, final_signal, color='#10b981', lw=2, label='Bio-Pulse-01')

# 🌟 关键：绘制半透明填充区域，营造渐变发光感
ax.fill_between(t, final_signal, bias, color='#10b981', alpha=0.15)

# 4. 图表细节装饰
ax.set_title("BIOMETRIC SPECTRUM ANALYSIS", color='#10b981', fontsize=10, pad=15, weight='bold')
ax.grid(color='#18181b', linestyle='--', linewidth=0.5)

# 隐藏边框，只留坐标轴颜色
for spine in ax.spines.values():
    spine.set_edgecolor('#27272a')

ax.tick_params(colors='#52525b', labelsize=8)
ax.legend(facecolor='#000000', edgecolor='#27272a', fontsize=8)

plt.tight_layout()

# 5. 内存转储与返回
buf = io.BytesIO()
plt.savefig(buf, format="png", dpi=120, bbox_inches='tight')
plt.close(fig)
buf.seek(0)
img_str = base64.b64encode(buf.read()).decode("utf-8")

f"data:image/png;base64,{img_str}"`} 
/>
SECOND TEST
<PythonViz 
  packages={["numpy", "matplotlib"]}
  code={`print("终")`} 
/>
结束
