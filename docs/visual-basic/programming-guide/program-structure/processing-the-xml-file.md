---
title: 處理 XML 檔案
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 9e12f6f5d86957a7f9aaea6047a79957fac8ce1e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072128"
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="f9557-102">處理 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9557-102">Processing the XML File (Visual Basic)</span></span>

<span data-ttu-id="f9557-103">編譯器會針對程式碼中，標記為要產生文件的每個建構產生識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="f9557-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="f9557-104"> (需如何標記程式碼的詳細資訊，請參閱 [XML 註解標記](../../language-reference/xmldoc/index.md)。 ) 識別碼字串可唯一識別此結構。</span><span class="sxs-lookup"><span data-stu-id="f9557-104">(For information on how to tag your code, see [XML Comment Tags](../../language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="f9557-105">處理 XML 檔案的程式可以使用識別碼字串來識別對應的 .NET Framework 中繼資料/反映專案。</span><span class="sxs-lookup"><span data-stu-id="f9557-105">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.</span></span>  
  
 <span data-ttu-id="f9557-106">XML 檔案不是程式碼的階層式標記法;它是具有針對每個元素產生之識別碼的一般清單。</span><span class="sxs-lookup"><span data-stu-id="f9557-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="f9557-107">編譯器在產生識別碼字串時會遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="f9557-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
- <span data-ttu-id="f9557-108">字串中未放置任何空白字元。</span><span class="sxs-lookup"><span data-stu-id="f9557-108">No white space is placed in the string.</span></span>  
  
- <span data-ttu-id="f9557-109">識別碼字串的第一個部分會識別所識別的成員種類，格式為單一字元後面接著一個冒號。</span><span class="sxs-lookup"><span data-stu-id="f9557-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="f9557-110">使用的是下列成員類型。</span><span class="sxs-lookup"><span data-stu-id="f9557-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="f9557-111">字元</span><span class="sxs-lookup"><span data-stu-id="f9557-111">Character</span></span>|<span data-ttu-id="f9557-112">描述</span><span class="sxs-lookup"><span data-stu-id="f9557-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="f9557-113">N</span><span class="sxs-lookup"><span data-stu-id="f9557-113">N</span></span>|<span data-ttu-id="f9557-114">namespace</span><span class="sxs-lookup"><span data-stu-id="f9557-114">namespace</span></span><br /><br /> <span data-ttu-id="f9557-115">您無法將檔批註新增至命名空間，但在支援的情況下，您可以對其進行 CREF 參考。</span><span class="sxs-lookup"><span data-stu-id="f9557-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="f9557-116">T</span><span class="sxs-lookup"><span data-stu-id="f9557-116">T</span></span>|<span data-ttu-id="f9557-117">類型： `Class` 、 `Module` 、 `Interface` 、 `Structure` 、 `Enum` 、 `Delegate`</span><span class="sxs-lookup"><span data-stu-id="f9557-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="f9557-118">F</span><span class="sxs-lookup"><span data-stu-id="f9557-118">F</span></span>|<span data-ttu-id="f9557-119">領域： `Dim`</span><span class="sxs-lookup"><span data-stu-id="f9557-119">field: `Dim`</span></span>|  
|<span data-ttu-id="f9557-120">P</span><span class="sxs-lookup"><span data-stu-id="f9557-120">P</span></span>|<span data-ttu-id="f9557-121">屬性： `Property` (包括預設屬性) </span><span class="sxs-lookup"><span data-stu-id="f9557-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="f9557-122">M</span><span class="sxs-lookup"><span data-stu-id="f9557-122">M</span></span>|<span data-ttu-id="f9557-123">方法： `Sub` 、 `Function` 、 `Declare` 、 `Operator`</span><span class="sxs-lookup"><span data-stu-id="f9557-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="f9557-124">E</span><span class="sxs-lookup"><span data-stu-id="f9557-124">E</span></span>|<span data-ttu-id="f9557-125">事件： `Event`</span><span class="sxs-lookup"><span data-stu-id="f9557-125">event: `Event`</span></span>|  
|<span data-ttu-id="f9557-126">!</span><span class="sxs-lookup"><span data-stu-id="f9557-126">!</span></span>|<span data-ttu-id="f9557-127">錯誤字串</span><span class="sxs-lookup"><span data-stu-id="f9557-127">error string</span></span><br /><br /> <span data-ttu-id="f9557-128">字串的其餘部分提供與錯誤相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="f9557-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="f9557-129">Visual Basic 編譯器會針對無法解析的連結產生錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="f9557-129">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
- <span data-ttu-id="f9557-130">的第二個部分 `String` 是專案的完整名稱，從命名空間的根目錄開始。</span><span class="sxs-lookup"><span data-stu-id="f9557-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="f9557-131">專案的名稱、其封入類型 (s) ，而且命名空間會以句號分隔。</span><span class="sxs-lookup"><span data-stu-id="f9557-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="f9557-132">如果專案本身的名稱包含句點，則會以數位記號取代 ( # ) 。</span><span class="sxs-lookup"><span data-stu-id="f9557-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="f9557-133">假設沒有任何專案會直接在其名稱中包含數位記號。</span><span class="sxs-lookup"><span data-stu-id="f9557-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="f9557-134">例如，此函式的完整名稱 `String` 就是 `System.String.#ctor` 。</span><span class="sxs-lookup"><span data-stu-id="f9557-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
- <span data-ttu-id="f9557-135">針對屬性和方法，如果有方法的引數，則後面會接著以括弧括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="f9557-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="f9557-136">如果沒有任何引數，就不會出現括弧。</span><span class="sxs-lookup"><span data-stu-id="f9557-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="f9557-137">引數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="f9557-137">The arguments are separated by commas.</span></span> <span data-ttu-id="f9557-138">每個引數的編碼方式會直接遵循 .NET Framework 簽章中的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f9557-138">The encoding of each argument follows directly how it is encoded in a .NET Framework signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9557-139">範例</span><span class="sxs-lookup"><span data-stu-id="f9557-139">Example</span></span>  

 <span data-ttu-id="f9557-140">下列程式碼顯示如何產生類別及其成員的識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="f9557-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="f9557-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9557-141">See also</span></span>

- [<span data-ttu-id="f9557-142">-doc</span><span class="sxs-lookup"><span data-stu-id="f9557-142">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="f9557-143">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="f9557-143">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
