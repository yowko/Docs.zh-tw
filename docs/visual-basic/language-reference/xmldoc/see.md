---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 51eaaef2ddb88afbb52ab58b85ed1a58ba251c1e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866454"
---
# <a name="see-visual-basic"></a><span data-ttu-id="cb1ed-101">\<see> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb1ed-101">\<see> (Visual Basic)</span></span>

<span data-ttu-id="cb1ed-102">指定另一個成員的連結。</span><span class="sxs-lookup"><span data-stu-id="cb1ed-102">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb1ed-103">語法</span><span class="sxs-lookup"><span data-stu-id="cb1ed-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb1ed-104">參數</span><span class="sxs-lookup"><span data-stu-id="cb1ed-104">Parameters</span></span>  

 `member`  
 <span data-ttu-id="cb1ed-105">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="cb1ed-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="cb1ed-106">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="cb1ed-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="cb1ed-107">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="cb1ed-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb1ed-108">備註</span><span class="sxs-lookup"><span data-stu-id="cb1ed-108">Remarks</span></span>  

 <span data-ttu-id="cb1ed-109">使用 `<see>` 標記可指定文字內的連結。</span><span class="sxs-lookup"><span data-stu-id="cb1ed-109">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="cb1ed-110">用 [\<seealso>](seealso.md) 來表示您可能想要在 [另請看] 區段中顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="cb1ed-110">Use [\<seealso>](seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="cb1ed-111">使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。</span><span class="sxs-lookup"><span data-stu-id="cb1ed-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb1ed-112">範例</span><span class="sxs-lookup"><span data-stu-id="cb1ed-112">Example</span></span>  

 <span data-ttu-id="cb1ed-113">此範例會使用 `<see>` [備註] 區段中的標記 `UpdateRecord` 來參考 `DoesRecordExist` 方法。</span><span class="sxs-lookup"><span data-stu-id="cb1ed-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="cb1ed-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb1ed-114">See also</span></span>

- [<span data-ttu-id="cb1ed-115">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="cb1ed-115">XML Comment Tags</span></span>](index.md)
