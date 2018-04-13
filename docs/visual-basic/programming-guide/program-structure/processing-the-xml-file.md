---
title: 處理 XML 檔案 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d44f58951d99f1b4b551af75dc0a0e895e337e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="26466-102">處理 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26466-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="26466-103">編譯器會針對程式碼中，標記為要產生文件的每個建構產生識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="26466-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="26466-104">(如需如何標記您的程式碼的資訊，請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)。)識別碼字串可唯一識別此建構。</span><span class="sxs-lookup"><span data-stu-id="26466-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="26466-105">處理 XML 檔案的程式可以使用來識別對應的識別碼字串[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]中繼資料/反映項目。</span><span class="sxs-lookup"><span data-stu-id="26466-105">Programs that process the XML file can use the ID string to identify the corresponding [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metadata/reflection item.</span></span>  
  
 <span data-ttu-id="26466-106">XML 檔案不是以階層方式呈現您的程式碼;它是以每個項目產生的識別碼為一般清單。</span><span class="sxs-lookup"><span data-stu-id="26466-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="26466-107">編譯器在產生識別碼字串時會遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="26466-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
-   <span data-ttu-id="26466-108">沒有泛空白字元被放在字串中。</span><span class="sxs-lookup"><span data-stu-id="26466-108">No white space is placed in the string.</span></span>  
  
-   <span data-ttu-id="26466-109">ID 字串的第一個部分會識別所識別，以單一字元，後面接著冒號成員種類。</span><span class="sxs-lookup"><span data-stu-id="26466-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="26466-110">會使用下列的成員類型。</span><span class="sxs-lookup"><span data-stu-id="26466-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="26466-111">字元</span><span class="sxs-lookup"><span data-stu-id="26466-111">Character</span></span>|<span data-ttu-id="26466-112">描述</span><span class="sxs-lookup"><span data-stu-id="26466-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="26466-113">N</span><span class="sxs-lookup"><span data-stu-id="26466-113">N</span></span>|<span data-ttu-id="26466-114">namespace</span><span class="sxs-lookup"><span data-stu-id="26466-114">namespace</span></span><br /><br /> <span data-ttu-id="26466-115">您無法將文件註解加入命名空間，但您可以進行 CREF 參考這些有支援。</span><span class="sxs-lookup"><span data-stu-id="26466-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="26466-116">T</span><span class="sxs-lookup"><span data-stu-id="26466-116">T</span></span>|<span data-ttu-id="26466-117">類型： `Class`， `Module`， `Interface`， `Structure`， `Enum`，`Delegate`</span><span class="sxs-lookup"><span data-stu-id="26466-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="26466-118">F</span><span class="sxs-lookup"><span data-stu-id="26466-118">F</span></span>|<span data-ttu-id="26466-119">欄位：`Dim`</span><span class="sxs-lookup"><span data-stu-id="26466-119">field: `Dim`</span></span>|  
|<span data-ttu-id="26466-120">P</span><span class="sxs-lookup"><span data-stu-id="26466-120">P</span></span>|<span data-ttu-id="26466-121">屬性： `Property` （包括預設屬性）</span><span class="sxs-lookup"><span data-stu-id="26466-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="26466-122">M</span><span class="sxs-lookup"><span data-stu-id="26466-122">M</span></span>|<span data-ttu-id="26466-123">方法： `Sub`， `Function`， `Declare`，`Operator`</span><span class="sxs-lookup"><span data-stu-id="26466-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="26466-124">E</span><span class="sxs-lookup"><span data-stu-id="26466-124">E</span></span>|<span data-ttu-id="26466-125">事件：`Event`</span><span class="sxs-lookup"><span data-stu-id="26466-125">event: `Event`</span></span>|  
|<span data-ttu-id="26466-126">!</span><span class="sxs-lookup"><span data-stu-id="26466-126">!</span></span>|<span data-ttu-id="26466-127">錯誤字串</span><span class="sxs-lookup"><span data-stu-id="26466-127">error string</span></span><br /><br /> <span data-ttu-id="26466-128">字串的其餘部分提供與錯誤相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="26466-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="26466-129">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器會產生無法解析的連結資訊時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="26466-129">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler generates error information for links that cannot be resolved.</span></span>|  
  
-   <span data-ttu-id="26466-130">第二個部分`String`是項目，從命名空間的根目錄開始的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="26466-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="26466-131">項目、 其封入類型，和命名空間名稱，並以句號分隔。</span><span class="sxs-lookup"><span data-stu-id="26466-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="26466-132">如果項目本身的名稱包含句點，它們被數字符號 （#）。</span><span class="sxs-lookup"><span data-stu-id="26466-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="26466-133">它會假設沒有項目，直接在其名稱中有數字的符號。</span><span class="sxs-lookup"><span data-stu-id="26466-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="26466-134">例如，完整的名稱的`String`建構函式會`System.String.#ctor`。</span><span class="sxs-lookup"><span data-stu-id="26466-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
-   <span data-ttu-id="26466-135">針對屬性和方法，如果有方法的引數，則後面會接著以括弧括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="26466-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="26466-136">如果沒有任何引數，就不會出現括弧。</span><span class="sxs-lookup"><span data-stu-id="26466-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="26466-137">引數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="26466-137">The arguments are separated by commas.</span></span> <span data-ttu-id="26466-138">每個引數的編碼方式會遵循直接如何編碼中[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]簽章。</span><span class="sxs-lookup"><span data-stu-id="26466-138">The encoding of each argument follows directly how it is encoded in a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26466-139">範例</span><span class="sxs-lookup"><span data-stu-id="26466-139">Example</span></span>  
 <span data-ttu-id="26466-140">下列程式碼將示範如何的 ID 字串類別，並產生其成員。</span><span class="sxs-lookup"><span data-stu-id="26466-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="26466-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26466-141">See Also</span></span>  
 [<span data-ttu-id="26466-142">/doc</span><span class="sxs-lookup"><span data-stu-id="26466-142">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="26466-143">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="26466-143">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
