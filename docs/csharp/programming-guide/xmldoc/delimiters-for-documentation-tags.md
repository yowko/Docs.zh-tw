---
title: "文件標籤的分隔符號 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 文件標記的 /** */ 分隔符號"
  - "C# 文件的 /// 分隔符號"
  - "XML [C#], 分隔符號"
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 文件標籤的分隔符號 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

使用 XML 文件註解時會需要分隔符號，讓編譯器知道文件註解從何處開始和結束。  您可以使用下列幾種分隔符號，以搭配 XML 文件標記使用：  
  
 `///`  
 單行分隔符號。  這是顯示在文件範例中並且為 Visual C\# 專案範本所使用的形式。  如果在分隔符號之後有空白字元，該字元就不會包含在 XML 輸出中。  
  
> [!NOTE]
>  Visual Studio IDE 提供一種稱為智慧型註解編輯的功能，當您在程式碼編輯器中輸入 `///` 分隔符號之後，會自動插入 \<summary\> 和 \<\/summary\> 標記，並將游標移到這兩個標記之間。  請從專案屬性頁中的[格式、C\#、文字編輯器、選項](/visual-studio/ide/reference/options-text-editor-csharp-formatting)存取這項功能。  
  
 `/** */`  
 多行分隔符號。  
  
 當您使用 `/** */` 分隔符號時，有一些必須遵循的格式化規則。  
  
-   在包含 `/**` 分隔符號的程式碼行上，如果該行的其餘部分是空白字元，就不會以註解方式處理。  如果 `/**`  分隔符號後的第一個字元是空白字元，該字元就會被忽略，並會處理該程式碼行的其他內容。  否則，在 `/**` 分隔符號之後的所有內容，都會當做註解的一部分來處理。  
  
-   在包含 `*/` 分隔符號的程式碼行上，如果 `*/` 分隔符號之前只有空白字元，就會忽略該行。  否則，在 `*/` 分隔符號之前，程式碼行的文字將會當做註解的一部分來處理，並受制於下列項目符號中所描述的模式比對規則。  
  
-   對於以 `/**` 分隔符號開頭一行之後的各行，編譯器都會在每一行的開頭尋找常見模式。  模式可以由選擇性的空白字元和星號 \(`*`\)，後接更多選擇性空白字元所組成。  如果編譯器發現每一行開頭的常見模式不是以 `/**` 分隔符號或 `*/` 分隔符號開始，就會忽略每一行的模式。  
  
 下列範例說明這些規則。  
  
-   下列註解中唯一會進行處理的部分，是以 `<summary>` 開頭的那行程式碼。  這三個標籤式會產生相同的註解。  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
  
    ```  
  
-   編譯器會識別第二列和第三列開頭的 " \* " 常用模式。  此模式不包含在輸出中。  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   編譯器在下列註解中找不到常用模式，因為第三列的第二個字元不是星號。  因此，第二列和第三列上的所有文字，都會被處理為註解的一部分。  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   因為兩個原因，編譯器無法在下列註解中找到任何模式。  首先，星號之前的空格數並不一致。  其次，第五行程式碼以標籤做為開頭，與空白字元不相符。  因此，從第二列到第五列的所有文字會被處理為註解的一部分。  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [XML 文件註解](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [XML 文件註解](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)