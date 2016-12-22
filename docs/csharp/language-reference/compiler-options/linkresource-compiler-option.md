---
title: "/linkresource (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/linkresource"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/linkresource compiler option [C#]"
  - "linkres compiler option [C#]"
  - "/linkres compiler option [C#]"
  - "-linkres compiler option [C#]"
  - "-linkresource compiler option [C#]"
  - "linkresource compiler option [C#]"
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /linkresource (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在輸出檔中建立 .NET Framework 資源的連結。  資源檔不會加入到輸出檔中。  這點與 [\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) 選項不同，該選項會將資源檔內嵌到輸出檔中。  
  
## 語法  
  
```  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## 引數  
 `filename`  
 您想要從該組件連結的 .NET Framework 資源檔。  
  
 `identifier` \(選擇項\)  
 資源的邏輯名稱，也就是用來載入資源的名稱。  預設值是檔案的名稱。  
  
 `accessibility-modifier` \(選擇項\)  
 資源的存取範圍︰public 或 private。  預設值為 public。  
  
## 備註  
 根據預設，當使用 C\# 編譯器建立連結資源時，組件中的連結資源會是公用的。  若要將資源設為私用的，請指定 `private` 做為存取範圍修飾詞。  不能使用 `public` 或 `private` 以外的其他修飾詞。  
  
 **\/linkresource** 需要 [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項其中之一，而非 **\/target:module**。  
  
 如果 `filename` 是由 [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) 或在開發環境中所建立的 .NET Framework 資源檔，則可以使用 <xref:System.Resources> 命名空間內的成員來存取。  如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager?displayProperty=fullName>。  至於其他所有資源，請使用 <xref:System.Reflection.Assembly> 類別中的 `GetManifestResource`\* 方法在執行階段存取資源。  
  
 在 `filename` 中指定的檔案可為任意格式。  例如，您可能希望讓原生 DLL 成為組件的一部分，以便將它安裝到全域組件快取，並經由組件中的 Managed 程式碼存取。  下列第二個範例示範其做法。  您可以在組件連結器中執行相同的操作。  下列第三個範例示範其做法。  如需詳細資訊，請參閱 [Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)和 [使用組件和全域組件快取](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md)。  
  
 **\/linkres** 是 **\/linkresource** 的簡短形式。  
  
 在 Visual Studio 中無法使用這個編譯器選項，而且無法利用程式設計的方式變更它。  
  
## 範例  
 編譯 `in.cs` 並將其連結至 `rf.resource` 資源檔：  
  
```  
csc /linkresource:rf.resource in.cs  
```  
  
## 範例  
 將 `A.cs` 編譯為 DLL、連結至原生 DLL N.dll，然後將輸出放入全域組件快取 \(GAC\) 中。  在這個範例中，A.dll 和 N.dll 都將位於 GAC 中。  
  
```  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## 範例  
 這個範例的做法與上一個範例相同，但使用的是「組件連結器」選項。  
  
```  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [使用組件和全域組件快取](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)