---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 3ca08016d3cef0c44e4f3c0bd0d017628eda606d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400043"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="95f4d-101">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95f4d-101">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="95f4d-102">將單字格式化為參數。</span><span class="sxs-lookup"><span data-stu-id="95f4d-102">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95f4d-103">語法</span><span class="sxs-lookup"><span data-stu-id="95f4d-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="95f4d-104">參數</span><span class="sxs-lookup"><span data-stu-id="95f4d-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="95f4d-105">要參考的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="95f4d-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="95f4d-106">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="95f4d-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95f4d-107">備註</span><span class="sxs-lookup"><span data-stu-id="95f4d-107">Remarks</span></span>  
 <span data-ttu-id="95f4d-108">`<paramref>`標記可讓您指定單字為參數。</span><span class="sxs-lookup"><span data-stu-id="95f4d-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="95f4d-109">可以處理 XML 檔案，以某種不同的方式來格式化此參數。</span><span class="sxs-lookup"><span data-stu-id="95f4d-109">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="95f4d-110">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="95f4d-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95f4d-111">範例</span><span class="sxs-lookup"><span data-stu-id="95f4d-111">Example</span></span>  
 <span data-ttu-id="95f4d-112">這個範例會使用 `<paramref>` 標記來參考 `id` 參數。</span><span class="sxs-lookup"><span data-stu-id="95f4d-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="95f4d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95f4d-113">See also</span></span>

- [<span data-ttu-id="95f4d-114">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="95f4d-114">XML Comment Tags</span></span>](index.md)
