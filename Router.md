



# Router Configuration

**Assign a name to the router**
`router(config)#hostname R1`

**Disable DNS lookup**
`router(config)#no ip domain lookup`

**Assign _class_ as a cipher password to EXEC privilege mode**
`router(config)#enable secrete class`

**Assign _cisco_ as the password for console mode and login**
`router(config)#line conosole 0`
`router(config-line)#password cisco`
`router(config-line)#login`

**Assign _cisco_ as the password for VTY mode and login**
`router(config)#line vty 0 4`
`router(config-line)#password cisco`
`router(config-line)#login`

**Encrypt the text password **
`router(config)#service password-encryption`

**Cree un aviso que advierta a todo el que acceda al dispositivo que el acceso no autorizado esta prohibido**
`router(config)#banner motd $ Authorized Users Only! $`

**Guardar la información en ejecución en el archivo de configuración de inicio**
`router#copy running-config startup-config`