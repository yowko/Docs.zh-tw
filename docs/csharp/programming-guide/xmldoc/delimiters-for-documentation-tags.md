---
title: "文件標籤的分隔符號 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0c72ee03ff8a2e28bec1ba83e42cd7f201b140ed
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a>文件標籤的分隔符號 (C# 程式設計手冊)
使用 XML 文件註解時需要分隔符號，以向編譯器指出文件註解的開始和結束位置。 您可以搭配使用下列類型的分隔符號與 XML 文件標記︰  
  
 `///`  
 單行分隔符號。 這是顯示在文件範例中並供 Visual C# 專案範本使用的表單。 如果分隔符號後面有空白字元，則該字元不會包括在 XML 輸出中。  
  
> [!NOTE]
>  Visual Studio IDE 有一項稱為「智慧註解編輯」的功能，可自動插入 \<summary> 和 \</summary> 標記，並在程式碼編輯器中輸入 `///` 分隔符號之後，將游標移至這些標記內。 您可以在 [[選項] 對話方塊](/visualstudio/ide/reference/options-text-editor-csharp-advanced)中開啟或關閉這項功能。  
  
 `/** */`  
 多行分隔符號。  
  
 使用 `/** */` 分隔符號時，可遵循一些格式規則。  
  
-   在包含 `/**` 分隔符號的行上，如果該行的其餘部分是空白字元，則不會處理該行的註解。 如果 `/**` 分隔符號後面的第一個字元是空白字元，則會忽略該空白字元，並處理該行的其餘部分。 否則，會將 `/**` 分隔符號後面的整行文字處理為註解的一部分。  
  
-   在包含 `*/` 分隔符號的行上，如果到 `*/` 分隔符號為止都只是空白字元，則會忽略該行。 否則，根據下列項目符號中所述的模式比對規則，會將到 `*/` 分隔符號為止的整行文字都處理為註解的一部分。  
  
-   針對在開頭為 `/**` 分隔符號之行後面的行，編譯器會尋找每行開頭的常見模式。 模式可以包含選擇性空白字元和星號 (`*`)，後面接著更多選擇性空白字元。 如果編譯器在開頭不是 `/**` 分隔符號或 `*/` 分隔符號的行開頭發現常見模式，則會忽略每行的該模式。  
  
 下列範例說明這些規則。  
  
-   下列註解中唯一會處理的部分是開頭為 `<summary>` 的那一行。 三個標記格式會產生相同的註解。  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   編譯器會識別第二行和第三行開頭的一般模式 "*"。 模式不會包括在輸出中。  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   因為第三行的第二個字元不是星號，所以編譯器在下列註解中找不到常見模式。 因此，會將第二行和第三行的所有文字都處理為註解的一部分。  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   基於兩個原因，編譯器在下列註解中找不到任何模式。 首先，星號前面的空格數目不一致。 其次，第五行的開頭是 Tab，這與空白字元不符。 因此，會將第二行到第五行的所有文字都處理為註解的一部分。  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [XML 文件註解](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [/doc (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [XML 文件註解](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
