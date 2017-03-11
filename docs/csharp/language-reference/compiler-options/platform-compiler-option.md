---
title: "/platform (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/platform"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "platform compiler option [C#]"
  - "-platform compiler option [C#]"
  - "/platform compiler option [C#]"
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: 46
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 46
---
# /platform (C# Compiler Options)
指定哪種版本的 Common Language Runtime \(CLR\) 可以執行組件。  
  
## 語法  
  
```  
/platform:string  
```  
  
#### 參數  
 `string`  
 anycpu \(預設值\)、anycpu32bitpreferred、 ARM、x64、x86或Itanium。  
  
## 備註  
  
-   **anycpu** \(預設值\) 會將組件編譯為可以在所有的平台上執行。  您的應用程式設定為盡可能以 64 位元處理序執行，並在只有此方式可用時會回到 32 位元。  
  
-   **anycpu32bitpreferred** 會編譯要在任何平台上執行的組件。  您的應用程式在支援 64 位元和 32 位元應用程式的系統上以 32 位元模式執行。  您可以針對以 .NET Framework 4.5 的專案中只指定這個選項。  
  
-   **ARM** 將組件編譯為可以在有進階 RISC 機器 \(ARM\) 處理器的電腦上執行。  
  
-   **x64** 會在支援 AMD64 或 EM64T 指令集的電腦上編譯將由 64 位元 Common Language Runtime 所執行的組件。  
  
-   **x86**會將組件編譯為可以由 32 位元的 x86 相容 Common Language Runtime 執行。  
  
-   **Itanium** 會將組件編譯為可以在使用 Itanium 處理器的電腦上、由 64 位元的 Common Language Runtime 執行。  
  
 在 64 位元的 Windows 作業系統上：  
  
-   以 **\/platform:x86** 編譯的組件會在以 WOW64 執行的 32 位元 CLR 上執行。  
  
-   以 **\/platform:anycpu** 編譯的 DLL 在與載入它的處理序同一個 CLR 上執行。  
  
-   在 64 位元的 CLR 上執行以 **\/platform:anycpu** 編譯的可執行檔。  
  
-   在 32 位元的 CLR 上執行以 **\/platform:anycpu32bitpreferred** 編譯的可執行檔。  
  
 **anycpu32bitpreferred** 設定為可執行檔 \(.EXE\) 檔案才有效，因此，它需要 .NET Framework 4.5。  
  
 如需開發可以在 Windows 64 位元作業系統上執行之應用程式的詳細資源，請參閱 [64 位元應用程式](../Topic/64-bit%20Applications.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  以 .NET Framework 4.5為目標的專案中，修改 \[**平台目標**\] 屬性和選取或清除 \[**32 位元的慣用方法。**\] 核取方塊。  
  
 **注意事項**  
 **\/platform** 無法在 Visual C\# Express 的開發環境中使用。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>。  
  
## 範例  
 下列範例顯示如何使用 **\/platform**選項，來指定應用程式只能在64 位元 Windows 作業系統上，由 64 位元 CLR 執行。  
  
```  
csc /platform:anycpu filename.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)