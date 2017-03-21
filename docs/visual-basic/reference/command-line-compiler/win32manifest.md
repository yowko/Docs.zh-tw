---
title: "/win32manifest (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b07d5816e5bb80a95e608fa7214a2db48ebac0dc
ms.lasthandoff: 03/13/2017

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
 根據預設，Visual Basic 編譯器會將內嵌指定 asInvoker 要求的執行層級的應用程式資訊清單。 它會建立資訊清單中的可執行檔建置完成後，通常當您使用 Visual Studio 的 bin\Debug 或 bin\Release 資料夾的相同資料夾中。 如果您想要提供自訂資訊清單，例如若要指定要求的執行層級 highestAvailable 或 requireAdministrator，使用此選項以指定的檔案名稱。  
  
> [!NOTE]
>  此選項和[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)是互斥的選項。 如果您嘗試在相同的命令列中使用這兩個選項，就會發生建置錯誤。  
  
 沒有資訊清單的任何應用程式的應用程式指定要求的執行層級會受限於檔案及登錄虛擬化在 Windows Vista 中的使用者帳戶控制功能。 如需虛擬化的詳細資訊，請參閱[Windows Vista 的 ClickOnce 部署](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista)。  
  
 如果下列條件時，您的應用程式會受制於虛擬化︰  
  
1.  您使用`/nowin32manifest`選項，且未提供的資訊清單中的更新版本的建置步驟或做為 Windows 資源 (.res) 檔案的一部分使用`/win32resource`選項。  
  
2.  您提供不會指定要求的執行層級的自訂資訊清單。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]建立預設.manifest 檔案，並將它儲存在與可執行檔在一起的偵錯和發行目錄中。 您可以檢視或編輯預設資訊清單檔案，請按一下**檢視 UAC 設定**上**應用程式**專案設計工具中的索引標籤。 如需詳細資訊，請參閱[應用程式] 頁面上，[專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
 您可以藉由提供應用程式資訊清單做為自訂的建置後步驟或 Win32 資源檔的`/nowin32manifest`選項。 如果您想受制於 Windows Vista 上的檔案或登錄虛擬化您的應用程式，請使用該相同的選項。 這會防止編譯器建立和內嵌在 PE 檔中的預設資訊清單。  
  
## <a name="example"></a>範例  
 下列範例會顯示 Visual Basic 編譯器插入 PE 預設資訊清單。  
  
> [!NOTE]
>  編譯器會插入 XML 資訊清單中的標準應用程式名稱 MyApplication.app。 這是因應措施，讓 Windows Server 2003 Service Pack 3 上執行的應用程式。  
  
```  
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
