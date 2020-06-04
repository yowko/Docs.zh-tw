---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 24358a1b004f1cefbfeb3fb8451380ed883841df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411469"
---
# <a name="value-visual-basic"></a><span data-ttu-id="7ffe4-101">\<value> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ffe4-101">\<value> (Visual Basic)</span></span>
<span data-ttu-id="7ffe4-102">指定屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="7ffe4-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ffe4-103">語法</span><span class="sxs-lookup"><span data-stu-id="7ffe4-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ffe4-104">參數</span><span class="sxs-lookup"><span data-stu-id="7ffe4-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="7ffe4-105">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="7ffe4-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ffe4-106">備註</span><span class="sxs-lookup"><span data-stu-id="7ffe4-106">Remarks</span></span>  
 <span data-ttu-id="7ffe4-107">使用 `<value>` 標記來描述屬性。</span><span class="sxs-lookup"><span data-stu-id="7ffe4-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="7ffe4-108">請注意，當您在 Visual Studio 開發環境中使用程式碼 wizard 加入屬性時，它會 [\<summary>](summary.md) 新增新屬性的標記。</span><span class="sxs-lookup"><span data-stu-id="7ffe4-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](summary.md) tag for the new property.</span></span> <span data-ttu-id="7ffe4-109">接著，您應該手動加入 `<value>` 標記來描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="7ffe4-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="7ffe4-110">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="7ffe4-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ffe4-111">範例</span><span class="sxs-lookup"><span data-stu-id="7ffe4-111">Example</span></span>  
 <span data-ttu-id="7ffe4-112">這個範例會使用 `<value>` 標記來描述屬性所保存的值 `Counter` 。</span><span class="sxs-lookup"><span data-stu-id="7ffe4-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7ffe4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ffe4-113">See also</span></span>

- [<span data-ttu-id="7ffe4-114">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="7ffe4-114">XML Comment Tags</span></span>](index.md)
