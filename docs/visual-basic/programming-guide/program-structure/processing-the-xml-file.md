---
title: 處理 XML 檔案 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 524a54443b8f2365252f11282ca29fc492bef351
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000229"
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="4508d-102">處理 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4508d-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="4508d-103">編譯器會針對程式碼中，標記為要產生文件的每個建構產生識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="4508d-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="4508d-104">(如需如何標記您的程式碼的資訊，請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)。)識別碼字串可唯一識別此建構。</span><span class="sxs-lookup"><span data-stu-id="4508d-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="4508d-105">處理 XML 檔案的程式可以使用識別碼字串，來識別對應[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]中繼資料/反映項目。</span><span class="sxs-lookup"><span data-stu-id="4508d-105">Programs that process the XML file can use the ID string to identify the corresponding [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metadata/reflection item.</span></span>  
  
 <span data-ttu-id="4508d-106">XML 檔案不是您的程式碼; 的階層式表示法它是與每個項目所產生之識別碼的一般清單。</span><span class="sxs-lookup"><span data-stu-id="4508d-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="4508d-107">編譯器在產生識別碼字串時會遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="4508d-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
-   <span data-ttu-id="4508d-108">字串中未放置任何空白字元。</span><span class="sxs-lookup"><span data-stu-id="4508d-108">No white space is placed in the string.</span></span>  
  
-   <span data-ttu-id="4508d-109">識別碼字串的第一個部分會識別所識別的成員種類，格式為單一字元後面接著一個冒號。</span><span class="sxs-lookup"><span data-stu-id="4508d-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="4508d-110">會使用下列的成員類型。</span><span class="sxs-lookup"><span data-stu-id="4508d-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="4508d-111">字元</span><span class="sxs-lookup"><span data-stu-id="4508d-111">Character</span></span>|<span data-ttu-id="4508d-112">描述</span><span class="sxs-lookup"><span data-stu-id="4508d-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="4508d-113">N</span><span class="sxs-lookup"><span data-stu-id="4508d-113">N</span></span>|<span data-ttu-id="4508d-114">namespace</span><span class="sxs-lookup"><span data-stu-id="4508d-114">namespace</span></span><br /><br /> <span data-ttu-id="4508d-115">您無法將文件註解加入命名空間，但是您可以讓 CREF 參考它們，其中支援。</span><span class="sxs-lookup"><span data-stu-id="4508d-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="4508d-116">T</span><span class="sxs-lookup"><span data-stu-id="4508d-116">T</span></span>|<span data-ttu-id="4508d-117">類型： `Class`， `Module`， `Interface`， `Structure`， `Enum`， `Delegate`</span><span class="sxs-lookup"><span data-stu-id="4508d-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="4508d-118">F</span><span class="sxs-lookup"><span data-stu-id="4508d-118">F</span></span>|<span data-ttu-id="4508d-119">欄位： `Dim`</span><span class="sxs-lookup"><span data-stu-id="4508d-119">field: `Dim`</span></span>|  
|<span data-ttu-id="4508d-120">P</span><span class="sxs-lookup"><span data-stu-id="4508d-120">P</span></span>|<span data-ttu-id="4508d-121">屬性： `Property` （包括預設屬性）</span><span class="sxs-lookup"><span data-stu-id="4508d-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="4508d-122">M</span><span class="sxs-lookup"><span data-stu-id="4508d-122">M</span></span>|<span data-ttu-id="4508d-123">方法： `Sub`， `Function`， `Declare`， `Operator`</span><span class="sxs-lookup"><span data-stu-id="4508d-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="4508d-124">E</span><span class="sxs-lookup"><span data-stu-id="4508d-124">E</span></span>|<span data-ttu-id="4508d-125">事件： `Event`</span><span class="sxs-lookup"><span data-stu-id="4508d-125">event: `Event`</span></span>|  
|<span data-ttu-id="4508d-126">!</span><span class="sxs-lookup"><span data-stu-id="4508d-126">!</span></span>|<span data-ttu-id="4508d-127">錯誤字串</span><span class="sxs-lookup"><span data-stu-id="4508d-127">error string</span></span><br /><br /> <span data-ttu-id="4508d-128">字串的其餘部分提供與錯誤相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="4508d-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="4508d-129">Visual Basic 編譯器會產生無法解析的連結資訊時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4508d-129">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
-   <span data-ttu-id="4508d-130">第二個部分`String`是項目，在命名空間的根開始的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="4508d-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="4508d-131">項目、 其封入的類型和命名空間的名稱並以句號分隔。</span><span class="sxs-lookup"><span data-stu-id="4508d-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="4508d-132">如果項目本身的名稱包含句點，它們會被取代的數字符號 （#）。</span><span class="sxs-lookup"><span data-stu-id="4508d-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="4508d-133">它會假設沒有項目，直接在其名稱中有數字的符號。</span><span class="sxs-lookup"><span data-stu-id="4508d-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="4508d-134">例如，完整的名稱的`String`建構函式會`System.String.#ctor`。</span><span class="sxs-lookup"><span data-stu-id="4508d-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
-   <span data-ttu-id="4508d-135">針對屬性和方法，如果有方法的引數，則後面會接著以括弧括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="4508d-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="4508d-136">如果沒有任何引數，就不會出現括弧。</span><span class="sxs-lookup"><span data-stu-id="4508d-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="4508d-137">引數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="4508d-137">The arguments are separated by commas.</span></span> <span data-ttu-id="4508d-138">每個引數的編碼方式都會直接遵循它中的編碼方式[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]簽章。</span><span class="sxs-lookup"><span data-stu-id="4508d-138">The encoding of each argument follows directly how it is encoded in a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4508d-139">範例</span><span class="sxs-lookup"><span data-stu-id="4508d-139">Example</span></span>  
 <span data-ttu-id="4508d-140">下列程式碼會顯示類別識別碼字串的方式，並產生其成員。</span><span class="sxs-lookup"><span data-stu-id="4508d-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4508d-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4508d-141">See Also</span></span>  
 [<span data-ttu-id="4508d-142">/doc</span><span class="sxs-lookup"><span data-stu-id="4508d-142">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="4508d-143">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="4508d-143">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
