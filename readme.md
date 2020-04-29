# CUPS backend for ZPL
> Print ZPL code to text file and render it to PDF using [http://labelary.com](http://labelary.com)

## Install
Install CUPS backend:
```
sudo cp cups-zpl /usr/lib/cups/backend
sudo chmod a+x /usr/lib/cups/backend/cups-zpl
sudo systemctl restart cups
```
Make sure the backend is registered by running `lpinfo -v`

Add printer 
```
lpadmin -p ZPL -v cups-zpl:/ -E
mkdir ~/PDF
chmod 777 ~/PDF
```

## Usage
```
echo "^XA^FO100, 200^AD,50,25^FH_^FD Hello world^FS^XZ" | lp -d ZPL
```

If everything works as expected, you should find the print in ~/PDF.

Inspect the log file `/tmp/cups-zpl.log` if you run into problems.