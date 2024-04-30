### Realme GET-OTA Script

```
sudo apt install python3-pip
```
```
python3 -m venv .venv
```
```
source .venv/bin/activate
```
```
pip3 install --upgrade git+https://github.com/R0rt1z2/realme-ota
```

- -r (GL = 0, CN = 1, IN= 2, EU = 3)
- -v (RUI - 1 , 2 , 3 , 4 , 5 )
- -d (Filename = [ Global = DUMPGL , China = DUMPCN , India = DUMPIN , Europe = DUMPEU ] )

```
realme-ota -r 0 RMX3301 RMX3301_11.F.00_0000_000000000000 5 -d DUMPGL.md
```
```
realme-ota -r 2 RMX3301 RMX3301_11.F.00_0000_000000000000 5 -d DUMPIN.md
```


## Click To Download


### Global

- [RMX3301_11.F.22 OTA DUMP](https://gauss-componentotacostmanual-sg.allawnofs.com/remove-d530d043bec503b835bcb5ede0f4f4ce/component-ota/24/02/23/188d97a61eba446ea32adc91942abddf.zip)

- [RMX3301_11.F.22 OTA INFO](https://gauss-componentotacostmanual-sg.allawnofs.com/remove-d530d043bec503b835bcb5ede0f4f4ce/component-ota/24/03/04/83c6ca9e37db4b48b9233638891826d1.html?logoType=1)

### India

- [RMX3301_11.F.22 OTA DUMP](https://gauss-componentotacostmanual-in.allawnofs.com/remove-d530d043bec503b835bcb5ede0f4f4ce/component-ota/24/02/23/188d97a61eba446ea32adc91942abddf.zip)

- [RMX3301_11.F.22 OTA INFO](https://gauss-componentotacostmanual-in.allawnofs.com/remove-d530d043bec503b835bcb5ede0f4f4ce/component-ota/24/03/04/83c6ca9e37db4b48b9233638891826d1.html?logoType=1)

## Extract images from OTA zip

```
https://github.com/ssut/payload-dumper-go.git
```

```
bash payload-dumper-go payload.bin
```

1. Extract the OTA zip file
2. Download and extract payload-dumper-go
3. Drag and drop payload.bin on payload-dumper-go executable

