---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: 4f31f1c32770d292f275354e0c06928e4677b7a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618605"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
識別要內嵌到專案的可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。  
  
## <a name="syntax"></a>語法  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`fileName`|自訂的資訊清單檔案的路徑。|  
  
## <a name="remarks"></a>備註  
 根據預設，Visual Basic 編譯器會內嵌應用程式資訊清單，指定 asInvoker 要求的執行層級。 它會建立資訊清單中的可執行檔建置時，通常是 bin\Debug 或 bin\Release 資料夾當您使用 Visual Studio 的相同資料夾中。 如果您想要提供自訂的資訊清單，例如若要指定要求的執行層級的 highestAvailable 或 requireAdministrator，使用此選項來指定檔案的名稱。  
  
> [!NOTE]
>  此選項， [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)選項互斥。 如果您嘗試在相同的命令列中使用這兩個選項，您會建置錯誤。  
  
 如果應用程式的應用程式資訊清單未指定要求的執行層級，則會受限於 Windows Vista 中「使用者帳戶控制」功能下的檔案/登錄虛擬化。 如需有關虛擬化的詳細資訊，請參閱 < [Windows Vista 的 ClickOnce 部署](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。  
  
 如果其中一個下列條件成立時，您的應用程式會受限於虛擬化：  
  
1.  您使用`-nowin32manifest`選項，而且未提供後面建置步驟中，或做為一部分的 Windows 資源 (.res) 檔案的資訊清單使用`-win32resource`選項。  
  
2.  您可以提供未指定所要求執行層級的自訂資訊清單。  
  
 Visual Studio 會建立預設.manifest 檔案，並將它與可執行檔一起儲存在偵錯和發行目錄中。 您可以檢視或編輯預設 app.manifest 檔案，依序按一下**檢視的 UAC 設定**上**應用程式**專案設計工具中的索引標籤。 如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
 您可以使用提供的應用程式資訊清單作為自訂建置後步驟或 Win32 資源檔的一部分`-nowin32manifest`選項。 如果您想要應用程式受制於 Windows Vista 上的檔案或登錄虛擬化，請使用這個相同的選項。 這會防止編譯器建立和內嵌預設資訊清單中的 PE 檔案。  
  
## <a name="example"></a>範例  
 下列範例將示範 Visual Basic 編譯器插入至 PE 的預設資訊清單。  
  
> [!NOTE]
>  編譯器會將標準應用程式名稱 MyApplication.app 插入資訊清單 XML。 這是讓應用程式在 Windows Server 2003 Service Pack 3 上執行的因應措施。  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
