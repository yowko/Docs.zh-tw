---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 3a2452ec60a2182adfee365777d9824001ff006a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400120"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="ebb0e-101">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebb0e-101">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="ebb0e-102">指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ebb0e-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebb0e-103">語法</span><span class="sxs-lookup"><span data-stu-id="ebb0e-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebb0e-104">參數</span><span class="sxs-lookup"><span data-stu-id="ebb0e-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="ebb0e-105">可從目前編譯環境取得之例外狀況的參考。</span><span class="sxs-lookup"><span data-stu-id="ebb0e-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="ebb0e-106">編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="ebb0e-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="ebb0e-107">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="ebb0e-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ebb0e-108">描述。</span><span class="sxs-lookup"><span data-stu-id="ebb0e-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebb0e-109">備註</span><span class="sxs-lookup"><span data-stu-id="ebb0e-109">Remarks</span></span>  
 <span data-ttu-id="ebb0e-110">使用 `<exception>` 標記來指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ebb0e-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="ebb0e-111">此標記會套用到方法定義。</span><span class="sxs-lookup"><span data-stu-id="ebb0e-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="ebb0e-112">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="ebb0e-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebb0e-113">範例</span><span class="sxs-lookup"><span data-stu-id="ebb0e-113">Example</span></span>  
 <span data-ttu-id="ebb0e-114">這個範例會使用 `<exception>` 標記來描述函式可以擲回的例外狀況 `IntDivide` 。</span><span class="sxs-lookup"><span data-stu-id="ebb0e-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ebb0e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebb0e-115">See also</span></span>

- [<span data-ttu-id="ebb0e-116">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="ebb0e-116">XML Comment Tags</span></span>](index.md)
