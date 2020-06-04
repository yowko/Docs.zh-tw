---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 5999a4ebcc90f21ee8331b96ffb2a50f7905b1b6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411508"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="917e8-101">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="917e8-101">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="917e8-102">指定出現在 [另請參閱] 區段中的連結。</span><span class="sxs-lookup"><span data-stu-id="917e8-102">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="917e8-103">語法</span><span class="sxs-lookup"><span data-stu-id="917e8-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="917e8-104">參數</span><span class="sxs-lookup"><span data-stu-id="917e8-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="917e8-105">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="917e8-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="917e8-106">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="917e8-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="917e8-107">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="917e8-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="917e8-108">備註</span><span class="sxs-lookup"><span data-stu-id="917e8-108">Remarks</span></span>  
 <span data-ttu-id="917e8-109">使用 `<seealso>` 標記來指定您想要顯示在 [另請參閱] 區段中的文字。</span><span class="sxs-lookup"><span data-stu-id="917e8-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="917e8-110">用 [\<see>](see.md) 來指定文字內的連結。</span><span class="sxs-lookup"><span data-stu-id="917e8-110">Use [\<see>](see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="917e8-111">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="917e8-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="917e8-112">範例</span><span class="sxs-lookup"><span data-stu-id="917e8-112">Example</span></span>  
 <span data-ttu-id="917e8-113">這個範例會使用 `<seealso>` [備註] 區段中的標記 `DoesRecordExist` 來參考 `UpdateRecord` 方法。</span><span class="sxs-lookup"><span data-stu-id="917e8-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="917e8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="917e8-114">See also</span></span>

- [<span data-ttu-id="917e8-115">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="917e8-115">XML Comment Tags</span></span>](index.md)
