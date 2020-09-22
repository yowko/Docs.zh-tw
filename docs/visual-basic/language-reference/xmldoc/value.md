---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 550f8b63928f80878ba316bfaf09077e14091305
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875172"
---
# <a name="value-visual-basic"></a><span data-ttu-id="5d6c2-101">\<value> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d6c2-101">\<value> (Visual Basic)</span></span>

<span data-ttu-id="5d6c2-102">指定屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="5d6c2-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d6c2-103">語法</span><span class="sxs-lookup"><span data-stu-id="5d6c2-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d6c2-104">參數</span><span class="sxs-lookup"><span data-stu-id="5d6c2-104">Parameters</span></span>  

 `property-description`  
 <span data-ttu-id="5d6c2-105">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="5d6c2-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d6c2-106">備註</span><span class="sxs-lookup"><span data-stu-id="5d6c2-106">Remarks</span></span>  

 <span data-ttu-id="5d6c2-107">使用 `<value>` 標記來描述屬性。</span><span class="sxs-lookup"><span data-stu-id="5d6c2-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="5d6c2-108">請注意，當您在 Visual Studio 開發環境中使用程式碼嚮導加入屬性時，它會 [\<summary>](summary.md) 新增新屬性的標記。</span><span class="sxs-lookup"><span data-stu-id="5d6c2-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](summary.md) tag for the new property.</span></span> <span data-ttu-id="5d6c2-109">然後，您應該手動新增 `<value>` 標記，以描述該屬性代表的值。</span><span class="sxs-lookup"><span data-stu-id="5d6c2-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="5d6c2-110">使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。</span><span class="sxs-lookup"><span data-stu-id="5d6c2-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d6c2-111">範例</span><span class="sxs-lookup"><span data-stu-id="5d6c2-111">Example</span></span>  

 <span data-ttu-id="5d6c2-112">此範例會使用 `<value>` 標記來描述屬性所保存的值 `Counter` 。</span><span class="sxs-lookup"><span data-stu-id="5d6c2-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5d6c2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d6c2-113">See also</span></span>

- [<span data-ttu-id="5d6c2-114">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="5d6c2-114">XML Comment Tags</span></span>](index.md)
