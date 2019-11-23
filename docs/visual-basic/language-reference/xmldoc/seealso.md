---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 27bb2c271631170082709d9e3d76cd39eefbc860
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352209"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="66094-101">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66094-101">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="66094-102">Specifies a link that appears in the See Also section.</span><span class="sxs-lookup"><span data-stu-id="66094-102">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66094-103">語法</span><span class="sxs-lookup"><span data-stu-id="66094-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="66094-104">參數</span><span class="sxs-lookup"><span data-stu-id="66094-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="66094-105">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="66094-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="66094-106">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="66094-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="66094-107">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="66094-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66094-108">備註</span><span class="sxs-lookup"><span data-stu-id="66094-108">Remarks</span></span>  
 <span data-ttu-id="66094-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span><span class="sxs-lookup"><span data-stu-id="66094-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="66094-110">使用 [\<see>](../../../visual-basic/language-reference/xmldoc/see.md)，以在文字內指定連結。</span><span class="sxs-lookup"><span data-stu-id="66094-110">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="66094-111">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="66094-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66094-112">範例</span><span class="sxs-lookup"><span data-stu-id="66094-112">Example</span></span>  
 <span data-ttu-id="66094-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span><span class="sxs-lookup"><span data-stu-id="66094-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="66094-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="66094-114">See also</span></span>

- [<span data-ttu-id="66094-115">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="66094-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
