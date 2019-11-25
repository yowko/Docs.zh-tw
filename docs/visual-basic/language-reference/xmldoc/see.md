---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 3c149b8ff60bcc2aba06856ad95f461fb18da4b6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352234"
---
# <a name="see-visual-basic"></a><span data-ttu-id="bfae0-101">\<see> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfae0-101">\<see> (Visual Basic)</span></span>
<span data-ttu-id="bfae0-102">Specifies a link to another member.</span><span class="sxs-lookup"><span data-stu-id="bfae0-102">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfae0-103">語法</span><span class="sxs-lookup"><span data-stu-id="bfae0-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfae0-104">參數</span><span class="sxs-lookup"><span data-stu-id="bfae0-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="bfae0-105">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="bfae0-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="bfae0-106">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="bfae0-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="bfae0-107">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="bfae0-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfae0-108">備註</span><span class="sxs-lookup"><span data-stu-id="bfae0-108">Remarks</span></span>  
 <span data-ttu-id="bfae0-109">Use the `<see>` tag to specify a link from within text.</span><span class="sxs-lookup"><span data-stu-id="bfae0-109">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="bfae0-110">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span><span class="sxs-lookup"><span data-stu-id="bfae0-110">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="bfae0-111">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="bfae0-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfae0-112">範例</span><span class="sxs-lookup"><span data-stu-id="bfae0-112">Example</span></span>  
 <span data-ttu-id="bfae0-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span><span class="sxs-lookup"><span data-stu-id="bfae0-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="bfae0-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="bfae0-114">See also</span></span>

- [<span data-ttu-id="bfae0-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="bfae0-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
