---
title: '檔標記的分隔符號-c # 程式設計手冊'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 7e62c75fd393c4009c987830cca41e512cdb6250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287378"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="a82af-102">檔標記的分隔符號（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="a82af-102">Delimiters for documentation tags (C# programming guide)</span></span>

<span data-ttu-id="a82af-103">使用 XML 文件註解時需要分隔符號，以向編譯器指出文件註解的開始和結束位置。</span><span class="sxs-lookup"><span data-stu-id="a82af-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="a82af-104">您可以搭配使用下列類型的分隔符號與 XML 文件標記︰</span><span class="sxs-lookup"><span data-stu-id="a82af-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>

- `///`

  <span data-ttu-id="a82af-105">單行分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a82af-105">Single-line delimiter.</span></span> <span data-ttu-id="a82af-106">這是顯示在檔範例中，並由 c # 專案範本所使用的表單。</span><span class="sxs-lookup"><span data-stu-id="a82af-106">This is the form that is shown in documentation examples and used by the C# project templates.</span></span> <span data-ttu-id="a82af-107">如果分隔符號後面有空白字元，則該字元不會包括在 XML 輸出中。</span><span class="sxs-lookup"><span data-stu-id="a82af-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>

  > [!NOTE]
  > <span data-ttu-id="a82af-108">在程式碼編輯器中輸入分隔符號之後，Visual Studio 整合式開發環境（IDE）會自動插入 `<summary>` 和 `</summary>` 標記，並將游標移到這些標記內 `///` 。</span><span class="sxs-lookup"><span data-stu-id="a82af-108">The Visual Studio integrated development environment (IDE) automatically inserts the `<summary>` and `</summary>` tags and moves your cursor within these tags after you type the `///` delimiter in the code editor.</span></span> <span data-ttu-id="a82af-109">您可以在 [[選項] 對話方塊](/visualstudio/ide/reference/options-text-editor-csharp-advanced)中開啟或關閉這項功能。</span><span class="sxs-lookup"><span data-stu-id="a82af-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>
  
- `/** */`

  <span data-ttu-id="a82af-110">多行分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a82af-110">Multiline delimiters.</span></span>

  <span data-ttu-id="a82af-111">當您使用分隔符號時，有一些要遵循的格式化規則 `/** */` ：</span><span class="sxs-lookup"><span data-stu-id="a82af-111">There are some formatting rules to follow when you use the `/** */` delimiters:</span></span>
  
  - <span data-ttu-id="a82af-112">在包含 `/**` 分隔符號的行上，如果該行的其餘部分是空白字元，則不會處理該行的註解。</span><span class="sxs-lookup"><span data-stu-id="a82af-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="a82af-113">如果 `/**` 分隔符號後面的第一個字元是空白字元，則會忽略該空白字元，並處理該行的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="a82af-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="a82af-114">否則，會將 `/**` 分隔符號後面的整行文字處理為註解的一部分。</span><span class="sxs-lookup"><span data-stu-id="a82af-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>

  - <span data-ttu-id="a82af-115">在包含 `*/` 分隔符號的行上，如果到 `*/` 分隔符號為止都只是空白字元，則會忽略該行。</span><span class="sxs-lookup"><span data-stu-id="a82af-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="a82af-116">否則，就會在批註中處理在分隔符號上的文字 `*/` 。</span><span class="sxs-lookup"><span data-stu-id="a82af-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment.</span></span>
  
  - <span data-ttu-id="a82af-117">針對在開頭為 `/**` 分隔符號之行後面的行，編譯器會尋找每行開頭的常見模式。</span><span class="sxs-lookup"><span data-stu-id="a82af-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="a82af-118">模式可以包含選擇性空白字元和星號 (`*`)，後面接著更多選擇性空白字元。</span><span class="sxs-lookup"><span data-stu-id="a82af-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="a82af-119">如果編譯器在開頭不是 `/**` 分隔符號或 `*/` 分隔符號的行開頭發現常見模式，則會忽略每行的該模式。</span><span class="sxs-lookup"><span data-stu-id="a82af-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>

  <span data-ttu-id="a82af-120">下列範例說明這些規則。</span><span class="sxs-lookup"><span data-stu-id="a82af-120">The following examples illustrate these rules.</span></span>

  - <span data-ttu-id="a82af-121">下列批註的唯一部分是以開頭的那一行 `<summary>` 。</span><span class="sxs-lookup"><span data-stu-id="a82af-121">The only part of the following comment that's processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="a82af-122">三個標記格式會產生相同的註解。</span><span class="sxs-lookup"><span data-stu-id="a82af-122">The three tag formats produce the same comments.</span></span>

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - <span data-ttu-id="a82af-123">編譯器會 \* 在第二個和第三行的開頭，識別一般的 "" 模式。</span><span class="sxs-lookup"><span data-stu-id="a82af-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="a82af-124">模式不會包括在輸出中。</span><span class="sxs-lookup"><span data-stu-id="a82af-124">The pattern is not included in the output.</span></span>

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - <span data-ttu-id="a82af-125">因為第三行的第二個字元不是星號，所以編譯器在下列註解中找不到常見模式。</span><span class="sxs-lookup"><span data-stu-id="a82af-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="a82af-126">因此，會將第二行和第三行的所有文字都處理為註解的一部分。</span><span class="sxs-lookup"><span data-stu-id="a82af-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - <span data-ttu-id="a82af-127">基於兩個原因，編譯器在下列註解中找不到任何模式。</span><span class="sxs-lookup"><span data-stu-id="a82af-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="a82af-128">首先，星號前面的空格數目不一致。</span><span class="sxs-lookup"><span data-stu-id="a82af-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="a82af-129">其次，第五行的開頭是 Tab，這與空白字元不符。</span><span class="sxs-lookup"><span data-stu-id="a82af-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="a82af-130">因此，會將第二行到第五行的所有文字都處理為註解的一部分。</span><span class="sxs-lookup"><span data-stu-id="a82af-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>

    <!-- markdownlint-disable MD010 -->
    ```csharp
    /**
      * <summary>
      * text
     *  text2
        *  </summary>
    */
    ```
    <!-- markdownlint-enable MD010 -->

## <a name="see-also"></a><span data-ttu-id="a82af-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a82af-131">See also</span></span>

- [<span data-ttu-id="a82af-132">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="a82af-132">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="a82af-133">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="a82af-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="a82af-134">-doc （c # 編譯器選項）</span><span class="sxs-lookup"><span data-stu-id="a82af-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
