---
title: "/win32manifest (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/win32manifest"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/win32manifest compiler option [C#]"
  - "win32manifest compiler option [C#]"
  - "-win32manifest compiler option [C#]"
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /win32manifest (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

使用 **\/win32manifest** 選項，指定將使用者定義的 Win32 應用程式資訊清單檔內嵌至專案的可攜式可執行 \(PE\) 檔。  
  
## 語法  
  
```  
/win32manifest: filename  
```  
  
## Arguments  
 `filename`  
 自訂資訊清單檔的名稱和位置。  
  
## 備註  
 [!INCLUDE[csharp_current_short](../../../csharp/language-reference/compiler-options/includes/csharp_current_short_md.md)] 編譯器 \(Compiler\) 預設會內嵌應用程式資訊清單，而這個資訊清單指定 "asInvoker" 要求的執行層級。編譯器會在建置執行檔所在的相同資料夾中建立資訊清單，使用 Visual Studio 時此資料夾通常是 bin\\Debug 或是 bin\\Release。  如果您要提供自訂資訊清單，例如指定 「highestAvailable」 或 「requireAdministrator」 所要求的執行層級，請使用此選項指定檔案名稱。  
  
> [!NOTE]
>  此選項和 [\/win32res \(Import a Win32 Resource File\)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) 選項是互斥 \(Mutually Exclusive\) 的選項。  如果您嘗試在相同命令列中同時使用兩個選項，會發生建置錯誤。  
  
 沒有應用程式資訊清單以指定要求的執行層級的應用程式，會受制於 Windows Vista 中「使用者帳戶控制」功能下的檔案\/登錄虛擬化。  如需虛擬化的詳細資訊，請參閱 [Windows Vista 開發人員小故事：Windows Vista 應用程式開發的使用者帳戶控制 \(UAC\) 需求](http://go.microsoft.com/fwlink/?LinkId=95452) 。  
  
 如果符合下列其中一個條件，應用程式便受制於虛擬化：  
  
-   使用 **\/nowin32manifest** 選項且未在稍後的建置步驟中提供資訊清單，或使用 **\/win32res** 選項提供資訊清單做為 Windows Resource \(.res\) 檔案的一部分。  
  
-   提供的自訂資訊清單未指定要求的執行層級。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 會建立預設的 .manifest 檔案，並儲存在與執行檔並列的偵錯和發行目錄中。  在任何文字編輯器中建立資訊清單，然後將檔案新增至專案，就可以新增自訂資訊清單。  您也可以用滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**專案**\] 圖示，然後按一下 \[**加入新項目**\]，再按一下 \[**應用程式資訊清單檔案**\]。  在您加入新的或現有的資訊清單檔之後，這個資訊清單檔會出現在 \[**資訊清單**\] 下拉式清單中。  如需詳細資訊，請參閱[專案設計工具，應用程式頁 \(C\#\)](/visual-studio/ide/reference/application-page-project-designer-csharp)。  
  
 您可以使用 [\/nowin32manifest \(No Win32 Manifest\)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) 選項，提供應用程式資訊清單做為自訂建置後步驟，或做為 Win32 資源檔的一部分。  如果您要應用程式受制於 Windows Vista 上的檔案或登錄虛擬化，也請使用這一個選項。  這樣會防止編譯器在可攜式可執行檔 \(PE\) 中建立和內嵌預設資訊清單。  
  
## 範例  
 下列範例顯示 Visual C\# 編譯器插入至 PE 的預設資訊清單。  
  
> [!NOTE]
>  編譯器會將標準應用程式名稱 " MyApplication.app " 插入至 xml。  這是讓應用程式在 Windows Server 2003 Service Pack 3 上執行的解決方法。  
  
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
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [\/nowin32manifest \(No Win32 Manifest\)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)