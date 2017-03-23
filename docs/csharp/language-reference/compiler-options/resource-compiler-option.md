---
title: "/resource (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/resource"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-resource compiler option [C#]"
  - "/resource compiler option [C#]"
  - "-res compiler option [C#]"
  - "/res compiler option [C#]"
  - "res compiler option [C#]"
  - "resource compiler option [C#]"
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# /resource (C# Compiler Options)
將指定的資源嵌入輸出檔。  
  
## 語法  
  
```  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## 引數  
 `filename`  
 您要嵌入輸出檔的 .NET Framework 資源檔。  
  
 `identifier` \(選擇項\)  
 資源的邏輯名稱，也就是用來載入資源的名稱。  預設名稱是檔名的名稱。  
  
 `accessibility-modifier` \(選擇項\)  
 資源的存取範圍︰public 或 private。  預設值為 public。  
  
## 備註  
 使用 [\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) 將資源連結至組件 \(Assembly\)，且不將資源檔加入輸出檔。  
  
 根據預設，當使用 C\# 編譯器建立組件中的連結資源時，這些資源會是公用的。  若要將資源設為私用的，請指定 `private` 做為存取範圍修飾詞。  不能使用 `public` 或 `private` 以外的其他存取範圍。  
  
 如果 `filename` 是由 [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) 或在開發環境中所建立的 .NET Framework 資源檔，則可以使用 <xref:System.Resources> 命名空間內的成員來存取。  如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager?displayProperty=fullName>。  至於其他所有資源，請使用 <xref:System.Reflection.Assembly> 類別中的 `GetManifestResource`\* 方法在執行階段存取資源。  
  
 **\/res** 是 **\/resource** 的簡短形式。  
  
 輸出檔中資源的順序是從命令列上指定的順序決定。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  將資源檔加入至您的專案。  
  
2.  在 \[**方案總管**\] 中，選取您想要內嵌的檔案。  
  
3.  在 \[**屬性**\] 視窗中選取檔案的 \[**建置動作**\]。  
  
4.  將 \[**建置動作**\] 設定為 \[**內嵌資源**\]。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.FileProperties2.BuildAction%2A>。  
  
## 範例  
 編譯 `in.cs` 並附加 `rf.resource` 資源檔：  
  
```  
csc /resource:rf.resource in.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)