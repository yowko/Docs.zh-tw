---
title: <value> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 516ff6ba534478d066b8ca06baee46bdd4b35265
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524612"
---
# <a name="value-visual-basic"></a><span data-ttu-id="8dd64-102">\<value > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="8dd64-102">\<value> (Visual Basic)</span></span>
<span data-ttu-id="8dd64-103">指定屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="8dd64-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd64-104">語法</span><span class="sxs-lookup"><span data-stu-id="8dd64-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dd64-105">參數</span><span class="sxs-lookup"><span data-stu-id="8dd64-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="8dd64-106">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="8dd64-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dd64-107">備註</span><span class="sxs-lookup"><span data-stu-id="8dd64-107">Remarks</span></span>  
 <span data-ttu-id="8dd64-108">使用 `<value>` 標記來描述屬性。</span><span class="sxs-lookup"><span data-stu-id="8dd64-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="8dd64-109">請注意，當您在 Visual Studio 開發環境中使用程式碼 wizard 加入屬性時，它會為新的屬性加入[\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md)標記。</span><span class="sxs-lookup"><span data-stu-id="8dd64-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="8dd64-110">接著，您應該手動加入 `<value>` 標記，以描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="8dd64-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="8dd64-111">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="8dd64-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dd64-112">範例</span><span class="sxs-lookup"><span data-stu-id="8dd64-112">Example</span></span>  
 <span data-ttu-id="8dd64-113">這個範例會使用 `<value>` 標記來描述 `Counter` 屬性所保存的值。</span><span class="sxs-lookup"><span data-stu-id="8dd64-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8dd64-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8dd64-114">See also</span></span>

- [<span data-ttu-id="8dd64-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="8dd64-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
