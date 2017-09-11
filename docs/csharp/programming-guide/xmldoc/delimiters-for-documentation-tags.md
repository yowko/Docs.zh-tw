---
title: "文件標籤的分隔符號 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3e31f0c3d815c0454a9be6813ff9a04e5fa4c7de
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="d1efa-102">文件標籤的分隔符號 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d1efa-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="d1efa-103">使用 XML 文件註解時需要分隔符號，以向編譯器指出文件註解的開始和結束位置。</span><span class="sxs-lookup"><span data-stu-id="d1efa-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="d1efa-104">您可以搭配使用下列類型的分隔符號與 XML 文件標記︰</span><span class="sxs-lookup"><span data-stu-id="d1efa-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="d1efa-105">單行分隔符號。</span><span class="sxs-lookup"><span data-stu-id="d1efa-105">Single-line delimiter.</span></span> <span data-ttu-id="d1efa-106">這是顯示在文件範例中並供 Visual C# 專案範本使用的表單。</span><span class="sxs-lookup"><span data-stu-id="d1efa-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="d1efa-107">如果分隔符號後面有空白字元，則該字元不會包括在 XML 輸出中。</span><span class="sxs-lookup"><span data-stu-id="d1efa-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1efa-108">Visual Studio IDE 有一項稱為「智慧註解編輯」的功能，可自動插入 \<summary> 和 \</summary> 標記，並在程式碼編輯器中輸入 `///` 分隔符號之後，將游標移至這些標記內。</span><span class="sxs-lookup"><span data-stu-id="d1efa-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="d1efa-109">從專案屬性頁面的[選項、文字編輯器、C#、格式](/visualstudio/ide/reference/options-text-editor-csharp-formatting)中，存取這項功能。</span><span class="sxs-lookup"><span data-stu-id="d1efa-109">Access this feature from the [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting) in your project property pages.</span></span>  
  
 `/** */`  
 <span data-ttu-id="d1efa-110">多行分隔符號。</span><span class="sxs-lookup"><span data-stu-id="d1efa-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="d1efa-111">使用 `/** */` 分隔符號時，可遵循一些格式規則。</span><span class="sxs-lookup"><span data-stu-id="d1efa-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
-   <span data-ttu-id="d1efa-112">在包含 `/**` 分隔符號的行上，如果該行的其餘部分是空白字元，則不會處理該行的註解。</span><span class="sxs-lookup"><span data-stu-id="d1efa-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="d1efa-113">如果 `/**` 分隔符號後面的第一個字元是空白字元，則會忽略該空白字元，並處理該行的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="d1efa-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="d1efa-114">否則，會將 `/**` 分隔符號後面的整行文字處理為註解的一部分。</span><span class="sxs-lookup"><span data-stu-id="d1efa-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
-   <span data-ttu-id="d1efa-115">在包含 `*/` 分隔符號的行上，如果到 `*/` 分隔符號為止都只是空白字元，則會忽略該行。</span><span class="sxs-lookup"><span data-stu-id="d1efa-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="d1efa-116">否則，根據下列項目符號中所述的模式比對規則，會將到 `*/` 分隔符號為止的整行文字都處理為註解的一部分。</span><span class="sxs-lookup"><span data-stu-id="d1efa-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
-   <span data-ttu-id="d1efa-117">針對在開頭為 `/**` 分隔符號之行後面的行，編譯器會尋找每行開頭的常見模式。</span><span class="sxs-lookup"><span data-stu-id="d1efa-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="d1efa-118">模式可以包含選擇性空白字元和星號 (`*`)，後面接著更多選擇性空白字元。</span><span class="sxs-lookup"><span data-stu-id="d1efa-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="d1efa-119">如果編譯器在開頭不是 `/**` 分隔符號或 `*/` 分隔符號的行開頭發現常見模式，則會忽略每行的該模式。</span><span class="sxs-lookup"><span data-stu-id="d1efa-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="d1efa-120">下列範例說明這些規則。</span><span class="sxs-lookup"><span data-stu-id="d1efa-120">The following examples illustrate these rules.</span></span>  
  
-   <span data-ttu-id="d1efa-121">下列註解中唯一會處理的部分是開頭為 `<summary>` 的那一行。</span><span class="sxs-lookup"><span data-stu-id="d1efa-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="d1efa-122">三個標記格式會產生相同的註解。</span><span class="sxs-lookup"><span data-stu-id="d1efa-122">The three tag formats produce the same comments.</span></span>  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   <span data-ttu-id="d1efa-123">編譯器會識別第二行和第三行開頭的一般模式 "*"。</span><span class="sxs-lookup"><span data-stu-id="d1efa-123">The compiler identifies a common pattern of " * " at the beginning of the second and third lines.</span></span> <span data-ttu-id="d1efa-124">模式不會包括在輸出中。</span><span class="sxs-lookup"><span data-stu-id="d1efa-124">The pattern is not included in the output.</span></span>  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   <span data-ttu-id="d1efa-125">因為第三行的第二個字元不是星號，所以編譯器在下列註解中找不到常見模式。</span><span class="sxs-lookup"><span data-stu-id="d1efa-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="d1efa-126">因此，會將第二行和第三行的所有文字都處理為註解的一部分。</span><span class="sxs-lookup"><span data-stu-id="d1efa-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   <span data-ttu-id="d1efa-127">基於兩個原因，編譯器在下列註解中找不到任何模式。</span><span class="sxs-lookup"><span data-stu-id="d1efa-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="d1efa-128">首先，星號前面的空格數目不一致。</span><span class="sxs-lookup"><span data-stu-id="d1efa-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="d1efa-129">其次，第五行的開頭是 Tab，這與空白字元不符。</span><span class="sxs-lookup"><span data-stu-id="d1efa-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="d1efa-130">因此，會將第二行到第五行的所有文字都處理為註解的一部分。</span><span class="sxs-lookup"><span data-stu-id="d1efa-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d1efa-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1efa-131">See Also</span></span>  
 <span data-ttu-id="d1efa-132">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d1efa-132">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d1efa-133">[XML 文件註解](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="d1efa-133">[XML Documentation Comments](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md) </span></span>  
 <span data-ttu-id="d1efa-134">[/doc (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="d1efa-134">[/doc (C# Compiler Options)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span></span>  
 [<span data-ttu-id="d1efa-135">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="d1efa-135">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)

