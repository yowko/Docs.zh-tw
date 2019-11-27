---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 240c2131179420834e6dade729ee631c0d7811a4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352178"
---
# <a name="value-visual-basic"></a><span data-ttu-id="74409-101">\<值 > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="74409-101">\<value> (Visual Basic)</span></span>
<span data-ttu-id="74409-102">指定屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="74409-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74409-103">語法</span><span class="sxs-lookup"><span data-stu-id="74409-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="74409-104">參數</span><span class="sxs-lookup"><span data-stu-id="74409-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="74409-105">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="74409-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74409-106">備註</span><span class="sxs-lookup"><span data-stu-id="74409-106">Remarks</span></span>  
 <span data-ttu-id="74409-107">使用 `<value>` 標記來描述屬性。</span><span class="sxs-lookup"><span data-stu-id="74409-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="74409-108">請注意，當您在 Visual Studio 開發環境中使用程式碼 wizard 加入屬性時，它會為新的屬性加入[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)標記。</span><span class="sxs-lookup"><span data-stu-id="74409-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="74409-109">接著，您應該手動加入 `<value>` 標記，以描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="74409-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="74409-110">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="74409-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74409-111">範例</span><span class="sxs-lookup"><span data-stu-id="74409-111">Example</span></span>  
 <span data-ttu-id="74409-112">這個範例會使用 `<value>` 標記來描述 `Counter` 屬性所保存的值。</span><span class="sxs-lookup"><span data-stu-id="74409-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="74409-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74409-113">See also</span></span>

- [<span data-ttu-id="74409-114">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="74409-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
