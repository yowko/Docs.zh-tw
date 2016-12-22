---
title: "/doc (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FileProperties.BuildAction"
  - "/doc"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "comments, C# code"
  - "XML documentation [C#], comments in source files"
  - "doc compiler option [C#]"
  - "Visual C#, XML documentation for"
  - "-doc compiler option [C#]"
  - "/doc compiler option [C#]"
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /doc (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/doc** 選項允許您將文件註解置於 XML 檔中。  
  
## 語法  
  
```  
/doc:file  
```  
  
## Arguments  
 `file`  
 XML 的輸出檔，它會填入 \(Populate\) 編譯的原始程式碼檔內的註解。  
  
## 備註  
 在原始程式碼檔中，可以處理位於下列項目前面的文件註解，並將其加入到 XML 檔中：  
  
-   諸如[類別](../../../csharp/language-reference/keywords/class.md)、[委派](../../../csharp/language-reference/keywords/delegate.md)或[介面](../../../csharp/language-reference/keywords/interface.md)等使用者定義型別  
  
-   諸如欄位、[事件](../../../csharp/language-reference/keywords/event.md)、[屬性](../../../csharp/programming-guide/classes-and-structs/using-properties.md)或方法等成員  
  
 包含 Main 的原始程式碼檔會先輸出至 XML。  
  
 若要將產生的 .xml 檔案運用於 [IntelliSense](/visual-studio/ide/using-intellisense) 功能，這個 .xml 檔案名稱就必須和您要支援的組件具有相同檔名，然後再確定此 .xml 檔案與該組件是位於相同的目錄中。  因此，在 Visual Studio 專案中參考組件時，同時也就可以找到 .xml 檔案。  如需詳細資訊，請參閱[提供程式碼註解](/visual-studio/ide/supplying-xml-code-comments)。  
  
 除非您使用 [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 編譯，否則 `file` 將會包含 \<assembly\>\<\/assembly\> 標記 \(Tag\)，以便指定其包含用編譯輸出檔的組建資訊清單之檔案名稱。  
  
> [!NOTE]
>  \/doc 選項會套用至所有輸入檔；如果在 \[專案設定\] 中設定該選項，則會套用至專案中的所有檔案。  若要停用特定檔案或程式碼區段的文件註解相關警告，請使用 [\#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)。  
  
 如需從程式碼的註解產生文件方法的詳細資訊，請參閱[建議的文件註解標記](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  
  
2.  按一下 \[**建置**\] 索引標籤。  
  
3.  修改 \[**XML 文件檔**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)