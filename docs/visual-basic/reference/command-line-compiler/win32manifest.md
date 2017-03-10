---
title: "/win32manifest (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/win32manifest compiler option [Visual Basic]"
  - "win32manifest compiler option [Visual Basic]"
  - "-win32manifest compiler option [Visual Basic]"
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# /win32manifest (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

識別使用者定義的 Win32 應用程式資訊清單檔，以便內嵌在專案的 PE 檔中。  
  
## 語法  
  
```  
/win32manifest: fileName  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`fileName`|自訂資訊清單檔的路徑。|  
  
## 備註  
 根據預設，Visual Basic 編譯器 \(Compiler\) 會內嵌應用程式資訊清單，該執行清單指定 asInvoker 要求的執行層級。  編譯器會在建置執行檔所在的相同資料夾中建立資訊清單，使用 Visual Studio 時此資料夾通常是 bin\\Debug or bin\\Release。  如果您要提供自訂資訊清單，例如指定 highestAvailable 或 requireAdministrator 要求的執行層級，請使用此選項指定檔案名稱。  
  
> [!NOTE]
>  此選項和 [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) 選項是互斥 \(Mutually Exclusive\) 的選項。  如果您嘗試在相同命令列中同時使用兩個選項，會發生建置錯誤。  
  
 沒有應用程式資訊清單以指定要求的執行層級的應用程式，會受制於 Windows Vista 中「使用者帳戶控制」功能下的檔案\/登錄虛擬化。  如需虛擬化的詳細資訊，請參閱 [Windows Vista 的 ClickOnce 部署](/visual-studio/deployment/clickonce-deployment-on-windows-vista)。  
  
 如果下列其中一個條件為真，您的應用程式便受制於虛擬化：  
  
1.  使用 `/nowin32manifest` 選項且未在稍後的建置步驟中提供資訊清單，或使用 `/win32resource` 選項提供資訊清單做為 Windows Resource \(.res\) 檔案的一部分。  
  
2.  提供的自訂資訊清單未指定要求的執行層級。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 會建立預設的 .manifest 檔案，並儲存在與執行檔並列的偵錯和發行目錄中。  您可以檢視或編輯預設的 app.manifest 檔案，方法是按一下 \[專案設計工具\] 中 \[**應用程式**\] 索引標籤上的 \[**檢視 UAC 設定**\]。如需詳細資訊，請參閱[應用程式頁面，專案設計工具 \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)。  
  
 您可以使用 `/nowin32manifest` 選項，提供應用程式資訊清單做為自訂建置後步驟，或做為 Win32 資源檔的一部分。  如果您要應用程式受制於 Windows Vista 上的檔案或登錄虛擬化，也請使用這一個選項。  這樣會防止編譯器在 PE 檔案中建立或內嵌預設資訊清單。  
  
## 範例  
 下列範例顯示 Visual Basic 編譯器插入至 PE 的預設資訊清單。  
  
> [!NOTE]
>  編譯器會將標準應用程式名稱 MyApplication.app 插入至資訊清單 XML。  這是讓應用程式在 Windows Server 2003 Service Pack 3 上執行的解決方法。  
  
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
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)