---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: 6eb9d50a3ecd80acb0349f1ba315d9cf8ccc6dc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937230"
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
|`fileName`|自訂資訊清單檔案的路徑。|  
  
## <a name="remarks"></a>備註  
 根據預設, Visual Basic 編譯器會內嵌應用程式資訊清單, 以指定所要求的執行層級 asInvoker。 它會在建立可執行檔的相同資料夾中建立資訊清單, 通常是使用 Visual Studio 時的 bin\Debug 或 bin\Release 資料夾。 如果您想要提供自訂資訊清單, 例如若要指定要求的執行層級為 highestAvailable 或 requireAdministrator, 請使用此選項來指定檔案名。  
  
> [!NOTE]
> 此選項和[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)選項是互斥的。 如果您嘗試在相同的命令列中使用這兩個選項, 您將會收到組建錯誤。  
  
 如果應用程式的應用程式資訊清單未指定要求的執行層級，則會受限於 Windows Vista 中「使用者帳戶控制」功能下的檔案/登錄虛擬化。 如需虛擬化的詳細資訊, 請參閱[Windows Vista 上的 ClickOnce 部署](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。  
  
 如果下列其中一個條件成立, 則您的應用程式會受限於虛擬化:  
  
1. 您可以使用`-nowin32manifest`選項, 而且您不會在稍後的組建步驟中提供資訊清單, 或`-win32resource`使用選項, 在 Windows 資源 (.res) 檔案的一部分。  
  
2. 您可以提供未指定所要求執行層級的自訂資訊清單。  
  
 Visual Studio 會建立預設.manifest 檔案，並將它與可執行檔一起儲存在偵錯和發行目錄中。 您可以在 [專案設計工具] 的 [**應用程式**] 索引標籤上, 按一下 [**查看 UAC 設定**], 以查看或編輯預設的應用程式。 如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
 您可以使用`-nowin32manifest`選項, 將應用程式資訊清單提供為自訂的後置組建步驟, 或做為 Win32 資源檔的一部分。 如果您想要應用程式受制於 Windows Vista 上的檔案或登錄虛擬化，請使用這個相同的選項。 這會防止編譯器在 PE 檔案中建立和內嵌預設資訊清單。  
  
## <a name="example"></a>範例  
 下列範例顯示 Visual Basic 編譯器插入 PE 的預設資訊清單。  
  
> [!NOTE]
> 編譯器會將標準應用程式名稱 MyApplication 插入資訊清單 XML。 這是讓應用程式在 Windows Server 2003 Service Pack 3 上執行的因應措施。  
  
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
