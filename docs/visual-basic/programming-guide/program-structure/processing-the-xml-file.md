---
title: 處理 XML 檔案
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 4230fd88b4b60c631135f5b7fb15f4b6272b5351
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347307"
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="9aabb-102">處理 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aabb-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="9aabb-103">編譯器會針對程式碼中，標記為要產生文件的每個建構產生識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="9aabb-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="9aabb-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span><span class="sxs-lookup"><span data-stu-id="9aabb-104">(For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="9aabb-105">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.</span><span class="sxs-lookup"><span data-stu-id="9aabb-105">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.</span></span>  
  
 <span data-ttu-id="9aabb-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span><span class="sxs-lookup"><span data-stu-id="9aabb-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="9aabb-107">編譯器在產生識別碼字串時會遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="9aabb-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
- <span data-ttu-id="9aabb-108">字串中未放置任何空白字元。</span><span class="sxs-lookup"><span data-stu-id="9aabb-108">No white space is placed in the string.</span></span>  
  
- <span data-ttu-id="9aabb-109">識別碼字串的第一個部分會識別所識別的成員種類，格式為單一字元後面接著一個冒號。</span><span class="sxs-lookup"><span data-stu-id="9aabb-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="9aabb-110">The following member types are used.</span><span class="sxs-lookup"><span data-stu-id="9aabb-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="9aabb-111">字元</span><span class="sxs-lookup"><span data-stu-id="9aabb-111">Character</span></span>|<span data-ttu-id="9aabb-112">描述</span><span class="sxs-lookup"><span data-stu-id="9aabb-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="9aabb-113">N</span><span class="sxs-lookup"><span data-stu-id="9aabb-113">N</span></span>|<span data-ttu-id="9aabb-114">namespace</span><span class="sxs-lookup"><span data-stu-id="9aabb-114">namespace</span></span><br /><br /> <span data-ttu-id="9aabb-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span><span class="sxs-lookup"><span data-stu-id="9aabb-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="9aabb-116">T</span><span class="sxs-lookup"><span data-stu-id="9aabb-116">T</span></span>|<span data-ttu-id="9aabb-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span><span class="sxs-lookup"><span data-stu-id="9aabb-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="9aabb-118">F</span><span class="sxs-lookup"><span data-stu-id="9aabb-118">F</span></span>|<span data-ttu-id="9aabb-119">field: `Dim`</span><span class="sxs-lookup"><span data-stu-id="9aabb-119">field: `Dim`</span></span>|  
|<span data-ttu-id="9aabb-120">P</span><span class="sxs-lookup"><span data-stu-id="9aabb-120">P</span></span>|<span data-ttu-id="9aabb-121">property: `Property` (including default properties)</span><span class="sxs-lookup"><span data-stu-id="9aabb-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="9aabb-122">M</span><span class="sxs-lookup"><span data-stu-id="9aabb-122">M</span></span>|<span data-ttu-id="9aabb-123">method: `Sub`, `Function`, `Declare`, `Operator`</span><span class="sxs-lookup"><span data-stu-id="9aabb-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="9aabb-124">E</span><span class="sxs-lookup"><span data-stu-id="9aabb-124">E</span></span>|<span data-ttu-id="9aabb-125">event: `Event`</span><span class="sxs-lookup"><span data-stu-id="9aabb-125">event: `Event`</span></span>|  
|<span data-ttu-id="9aabb-126">!</span><span class="sxs-lookup"><span data-stu-id="9aabb-126">!</span></span>|<span data-ttu-id="9aabb-127">錯誤字串</span><span class="sxs-lookup"><span data-stu-id="9aabb-127">error string</span></span><br /><br /> <span data-ttu-id="9aabb-128">字串的其餘部分提供與錯誤相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="9aabb-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="9aabb-129">The Visual Basic compiler generates error information for links that cannot be resolved.</span><span class="sxs-lookup"><span data-stu-id="9aabb-129">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
- <span data-ttu-id="9aabb-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span><span class="sxs-lookup"><span data-stu-id="9aabb-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="9aabb-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span><span class="sxs-lookup"><span data-stu-id="9aabb-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="9aabb-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span><span class="sxs-lookup"><span data-stu-id="9aabb-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="9aabb-133">It is assumed that no item has a number sign directly in its name.</span><span class="sxs-lookup"><span data-stu-id="9aabb-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="9aabb-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span><span class="sxs-lookup"><span data-stu-id="9aabb-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
- <span data-ttu-id="9aabb-135">針對屬性和方法，如果有方法的引數，則後面會接著以括弧括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="9aabb-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="9aabb-136">如果沒有任何引數，就不會出現括弧。</span><span class="sxs-lookup"><span data-stu-id="9aabb-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="9aabb-137">引數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="9aabb-137">The arguments are separated by commas.</span></span> <span data-ttu-id="9aabb-138">The encoding of each argument follows directly how it is encoded in a .NET Framework signature.</span><span class="sxs-lookup"><span data-stu-id="9aabb-138">The encoding of each argument follows directly how it is encoded in a .NET Framework signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aabb-139">範例</span><span class="sxs-lookup"><span data-stu-id="9aabb-139">Example</span></span>  
 <span data-ttu-id="9aabb-140">The following code shows how the ID strings for a class and its members are generated.</span><span class="sxs-lookup"><span data-stu-id="9aabb-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="9aabb-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="9aabb-141">See also</span></span>

- [<span data-ttu-id="9aabb-142">-doc</span><span class="sxs-lookup"><span data-stu-id="9aabb-142">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="9aabb-143">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="9aabb-143">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
