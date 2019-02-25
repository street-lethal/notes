# 分割 & 結合

## 分割
### Unix
```bash
split filename.iso -b 500m -d filename.iso_
```

## 結合
### Unix
```bash
cat filename.iso_* > filename.iso
```

### Windows
```
copy /b filename.iso_* filename.iso
```
