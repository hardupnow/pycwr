# pycwr (Python China Weather Radar tools libaray)

- [README in Chinese](README_CN.md)
- [Developers and contributors](CONTRIBUTORS.txt)

Project development plan
----------

- [x] WSR98D, CINRAD/SA/SB/CB, CINRAD/CC/CCJ, CINRAD/SC/CD support
- [ ] Cfradial Read support
- [x] Write to Cfradial support
- [x] Automatically identify radar and obtain latitude and longitude information (SA/SB/CB)
- [x] Automatic recognition of radar data format types
- [x] transform to Pyart Radar object
- [x] Graphical interface support
- [x] Radar vertical profile support
- [x] Interpolation algorithm support
- [x] PPI drawing support, overlay map support
- [ ] RHI drawing support
- [ ] Multi-radar inversion algorithm support
- [ ] Radar product algorithm support
- [ ] Doppler Radar/Dual polarization radar quality control algorithm
- [ ] DSD Algorithm Support for Dual Polarization Radar
- [ ] Doppler radar wind field retrieve support
- [ ] Radar quantitative precipitation estimation algorithm support
- [ ] Radar extrapolation algorithm support
- [ ] Radar quantitative precipitation forecast  algorithm support

Install pycwr Library
----------
### The easiest route to installing pycwr is through pip and conda:

if you haven't install cartopy, for all platforms installing cartopy can be done with:

```
conda install -c conda-forge cartopy
```
and you can install pycwr with pip:
```
pip install pycwr
```

### Also, you can install from source code:

```
git clone https://github.com/YvZheng/pycwr.git
cd pycwr
python setup.py install    
```

Read Radar Basedata to PRD (Polarimetry Radar Data) class or Py-ART Radar class
----------
```
from pycwr.io.auto_io import radar_io 
file = r"./Z_RADR_I_Z9898_20190828192401_O_DOR_SAD_CAP_FMT.bin.bz2"
data = radar_io(file)
PRD = data.ToPRD(withlatlon=True)
print(PRD.scan_info)
print(PRD.fields)
PyartRadar = data.ToPyartRadar()
```
The data structure of the PRD is as follows:

![avatar](./examples/PRD_class.png)

Plotting Radar Data with map
----------
```
from pycwr.draw.SingleRadarPlotMap import RadarGraphMap
graph = RadarGraphMap(PRD)
graph.plot(0, "dBZ")
plt.show()
```
As illustrated in the picture below:

![avatar](examples/graph_map.png)

Plotting VCS
----------
```
from pycwr.draw.VerticalSectionPlot import VerticalSection
vcs = VerticalSection(PRD)
vcs.section((0,0), (150, 0), "dBZ", (0, 10))  # (start_x, start_y), (end_x, end_y) units:km
plt.show()
```
![avatar](examples/vcs.png)

Launch Graphical interface to show Radar Data
----------

```
 python scripts/LaunchGUI.py
```

The main window opens as shown below:

![avatar](examples/pycwr.png)

more example via: [exmaple](./notebooks/pycwr_example.ipynb)

Developers and Contributors
----------

Yu Zheng - Nanjing University of Information Science and Technology, School of Atmospheric Physics

Nan Li - Nanjing University of Information Science and Technology, School of Atmospheric Physics

Wei Ming - Nanjing University of Information Science and Technology, School of Atmospheric Physics

Zhigang Chu - Nanjing University of Information Science and Technology, School of Atmospheric Physics

Sihui Fan - Nanjing University of Information Science and Technology, School of Atmospheric Physics

Pengcheng Jia - Nanjing University of Information Science and Technology, School of Atmospheric Physics

Yang Li - Nanjing University of Information Science and Technology, School of Atmospheric Physics

Xin Zhang  - Nanjing University of Information Science and Technology, School of Atmospheric Physics

Xingchao Lv - Nanjing University of Information Science and Technology, School of Atmospheric Physics


