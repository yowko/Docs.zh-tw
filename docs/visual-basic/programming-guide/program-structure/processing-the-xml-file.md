---
title: "處理 XML 檔案 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML comments, parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cf15cf59413e0e019086dd1a79951ccb212f037b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="f5e83-102">處理 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5e83-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="f5e83-103">編譯器產生的標記來產生文件程式碼中每個建構的識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="f5e83-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="f5e83-104">(有關如何標記程式碼的資訊，請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)。)ID 字串可唯一識別此建構。</span><span class="sxs-lookup"><span data-stu-id="f5e83-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="f5e83-105">處理 XML 檔案的程式可以使用識別碼字串來識別對應[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]中繼資料/反映項目。</span><span class="sxs-lookup"><span data-stu-id="f5e83-105">Programs that process the XML file can use the ID string to identify the corresponding [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] metadata/reflection item.</span></span>  
  
 <span data-ttu-id="f5e83-106">XML 檔案不是以階層方式呈現您的程式碼;它是以每個項目產生的識別碼為一般清單。</span><span class="sxs-lookup"><span data-stu-id="f5e83-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="f5e83-107">產生的識別碼字串時，編譯器會遵守下列規則︰</span><span class="sxs-lookup"><span data-stu-id="f5e83-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
-   <span data-ttu-id="f5e83-108">沒有泛空白字元被放在字串中。</span><span class="sxs-lookup"><span data-stu-id="f5e83-108">No white space is placed in the string.</span></span>  
  
-   <span data-ttu-id="f5e83-109">ID 字串的第一個部分會識別所識別，以單一字元，後面接著冒號成員種類。</span><span class="sxs-lookup"><span data-stu-id="f5e83-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="f5e83-110">使用下列的成員類型。</span><span class="sxs-lookup"><span data-stu-id="f5e83-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="f5e83-111">字元</span><span class="sxs-lookup"><span data-stu-id="f5e83-111">Character</span></span>|<span data-ttu-id="f5e83-112">描述</span><span class="sxs-lookup"><span data-stu-id="f5e83-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="f5e83-113">N</span><span class="sxs-lookup"><span data-stu-id="f5e83-113">N</span></span>|<span data-ttu-id="f5e83-114">namespace</span><span class="sxs-lookup"><span data-stu-id="f5e83-114">namespace</span></span><br /><br /> <span data-ttu-id="f5e83-115">您無法將文件註解加入至命名空間，但是您可以讓 CREF 參考這些支援。</span><span class="sxs-lookup"><span data-stu-id="f5e83-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="f5e83-116">T</span><span class="sxs-lookup"><span data-stu-id="f5e83-116">T</span></span>|<span data-ttu-id="f5e83-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`,`Delegate`</span><span class="sxs-lookup"><span data-stu-id="f5e83-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="f5e83-118">F</span><span class="sxs-lookup"><span data-stu-id="f5e83-118">F</span></span>|<span data-ttu-id="f5e83-119">欄位︰`Dim`</span><span class="sxs-lookup"><span data-stu-id="f5e83-119">field: `Dim`</span></span>|  
|<span data-ttu-id="f5e83-120">P</span><span class="sxs-lookup"><span data-stu-id="f5e83-120">P</span></span>|<span data-ttu-id="f5e83-121">屬性︰ `Property` （包括預設屬性）</span><span class="sxs-lookup"><span data-stu-id="f5e83-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="f5e83-122">M</span><span class="sxs-lookup"><span data-stu-id="f5e83-122">M</span></span>|<span data-ttu-id="f5e83-123">method: `Sub`, `Function`, `Declare`,`Operator`</span><span class="sxs-lookup"><span data-stu-id="f5e83-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="f5e83-124">E</span><span class="sxs-lookup"><span data-stu-id="f5e83-124">E</span></span>|<span data-ttu-id="f5e83-125">事件︰`Event`</span><span class="sxs-lookup"><span data-stu-id="f5e83-125">event: `Event`</span></span>|  
|<span data-ttu-id="f5e83-126">!</span><span class="sxs-lookup"><span data-stu-id="f5e83-126">!</span></span>|<span data-ttu-id="f5e83-127">錯誤字串</span><span class="sxs-lookup"><span data-stu-id="f5e83-127">error string</span></span><br /><br /> <span data-ttu-id="f5e83-128">字串的其餘內容提供錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f5e83-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="f5e83-129">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會產生無法解析的連結資訊時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f5e83-129">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler generates error information for links that cannot be resolved.</span></span>|  
  
-   <span data-ttu-id="f5e83-130">第二個部分`String`是開始於命名空間的根項目的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e83-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="f5e83-131">項目，其封入型別和命名空間名稱，並以句號分隔。</span><span class="sxs-lookup"><span data-stu-id="f5e83-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="f5e83-132">如果項目本身的名稱包含句點，它們被數字符號 （#）。</span><span class="sxs-lookup"><span data-stu-id="f5e83-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="f5e83-133">假設沒有項目，直接在其名稱中有數字的符號。</span><span class="sxs-lookup"><span data-stu-id="f5e83-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="f5e83-134">例如，完整的名稱的`String`建構函式會是`System.String.#ctor`。</span><span class="sxs-lookup"><span data-stu-id="f5e83-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
-   <span data-ttu-id="f5e83-135">屬性和方法，如果您有的方法引數括號括住的引數清單如下。</span><span class="sxs-lookup"><span data-stu-id="f5e83-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="f5e83-136">如果不有任何引數，沒有括號會出現。</span><span class="sxs-lookup"><span data-stu-id="f5e83-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="f5e83-137">引數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="f5e83-137">The arguments are separated by commas.</span></span> <span data-ttu-id="f5e83-138">每個引數的編碼方式會遵循直接如何在編碼[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]簽章。</span><span class="sxs-lookup"><span data-stu-id="f5e83-138">The encoding of each argument follows directly how it is encoded in a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5e83-139">範例</span><span class="sxs-lookup"><span data-stu-id="f5e83-139">Example</span></span>  
 <span data-ttu-id="f5e83-140">下列程式碼顯示針對類別 ID 字串的方式，並且會產生其成員。</span><span class="sxs-lookup"><span data-stu-id="f5e83-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 <span data-ttu-id="f5e83-141">[!code-vb[VbVbcnXmlDocComments #&10;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f5e83-141">[!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e83-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5e83-142">See Also</span></span>  
 <span data-ttu-id="f5e83-143">[/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span><span class="sxs-lookup"><span data-stu-id="f5e83-143">[/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span></span>  
<span data-ttu-id="f5e83-144"> [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="f5e83-144"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span></span>
