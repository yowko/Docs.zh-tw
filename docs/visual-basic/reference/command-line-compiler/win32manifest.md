---
title: /win32manifest (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a46641181c3ff66882468f8372bb97c3a49a8462
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="win32manifest-visual-basic"></a>/win32manifest (Visual Basic)
識別要內嵌到專案的可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。  
  
## <a name="syntax"></a>語法  
  
```  
/win32manifest: fileName  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`fileName`|自訂資訊清單檔案的路徑。|  
  
## <a name="remarks"></a>備註  
 根據預設，Visual Basic 編譯器會將內嵌指定 asInvoker 要求的執行層級的應用程式資訊清單。 它會建立資訊清單中的可執行檔建置時，通常是 bin\Debug 或是 bin\Release 資料夾當您使用 Visual Studio 的相同資料夾中。 如果您想要提供自訂資訊清單，例如若要指定要求的執行層級 highestAvailable 或 requireAdministrator，使用此選項來指定檔案的名稱。  
  
> [!NOTE]
>  此選項和[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)選項互斥。 如果您嘗試在相同的命令列中使用這兩個選項，就會發生建置錯誤。  
  
 如果應用程式的應用程式資訊清單未指定要求的執行層級，則會受限於 Windows Vista 中「使用者帳戶控制」功能下的檔案/登錄虛擬化。 如需虛擬化的詳細資訊，請參閱[ClickOnce 部署在 Windows Vista 上](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。  
  
 如果其中一個的下列條件成立，您的應用程式都會受到虛擬化：  
  
1.  您使用`/nowin32manifest`選項，且未提供的資訊清單中的更新版本的建置步驟或做為 Windows 資源 (.res) 檔案的一部分使用`/win32resource`選項。  
  
2.  您可以提供未指定所要求執行層級的自訂資訊清單。  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 會建立預設.manifest 檔案，並將它與可執行檔一起儲存在偵錯和發行目錄中。 您可以檢視，或按一下 編輯預設 app.manifest 檔案**檢視 UAC 設定**上**應用程式**專案設計工具中的索引標籤。 如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
 您可以使用提供的應用程式資訊清單做為自訂建置後步驟，或做為 Win32 資源檔的一部分`/nowin32manifest`選項。 如果您想要應用程式受制於 Windows Vista 上的檔案或登錄虛擬化，請使用這個相同的選項。 如此可防止編譯器建立和內嵌 PE 檔中的預設資訊清單。  
  
## <a name="example"></a>範例  
 下列範例會示範 Visual Basic 編譯器插入 PE 預設資訊清單。  
  
> [!NOTE]
>  編譯器會插入到資訊清單 XML 的標準應用程式名稱 MyApplication.app。 這是讓應用程式在 Windows Server 2003 Service Pack 3 上執行的因應措施。  
  
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
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
