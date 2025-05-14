## Vídeo de referência: [Como sincronizar seus usuários do Entra ID com seu AD Local - Soft Match x Hard Match](https://www.youtube.com/watch?v=24xdS658G80)

### Com a descontinuação do módulo **MSol**, atualmente a Microsoft está utilizando o módulo **Mg** - Microsoft Graph
---
~~Instalar o módulo de Entra ID (Azure AD): Install-Module MSOnline~~

**Instalar o módulo de Microsoft Graph**:

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser -Repository PSGallery -Force
```

**Importar o módulo de Microsoft Graph**: 

```powershell
Import-Module Microsoft.Graph -Scope CurrentUser
```

---

**Alterar variável MaximumVariableCount**: 
```powershell
$MaximumVariableCount = 10000
```
**Alterar variável MaximumFunctionCount**: 
```powershell
$MaximumFunctionCount = 10000
```
---

~~Conectar no Entra ID: Connect-MsolService~~

**Conectar no Entra ID**: 
```powershell
Connect-MgGraph -Scopes "User.Read.All" -TenantId "inclua-o-tenantid" -NoWelcome
```
---

~Validar o ImmutableID do usuário no Entra ID: Get-Msoluser -UserPrincipalName usuario@dominio | Select-Object ImmutableId~

**Validar o ImmutableID do usuário no Entra ID**: 
```powershell
Get-MgUser -UserId "nomedousuario@dominio" -Property "onPremisesImmutableId" | Select-Object onPremisesImmutableId
```
