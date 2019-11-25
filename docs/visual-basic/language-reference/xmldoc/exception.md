---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e1e7f2d0fb06599f83ba224ed52a10429d9b11fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346965"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="2934c-101">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2934c-101">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="2934c-102">Specifies which exceptions can be thrown.</span><span class="sxs-lookup"><span data-stu-id="2934c-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2934c-103">語法</span><span class="sxs-lookup"><span data-stu-id="2934c-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2934c-104">參數</span><span class="sxs-lookup"><span data-stu-id="2934c-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="2934c-105">可從目前編譯環境取得之例外狀況的參考。</span><span class="sxs-lookup"><span data-stu-id="2934c-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="2934c-106">編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="2934c-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="2934c-107">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="2934c-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="2934c-108">描述。</span><span class="sxs-lookup"><span data-stu-id="2934c-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2934c-109">備註</span><span class="sxs-lookup"><span data-stu-id="2934c-109">Remarks</span></span>  
 <span data-ttu-id="2934c-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span><span class="sxs-lookup"><span data-stu-id="2934c-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="2934c-111">此標記會套用到方法定義。</span><span class="sxs-lookup"><span data-stu-id="2934c-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="2934c-112">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="2934c-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2934c-113">範例</span><span class="sxs-lookup"><span data-stu-id="2934c-113">Example</span></span>  
 <span data-ttu-id="2934c-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span><span class="sxs-lookup"><span data-stu-id="2934c-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2934c-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="2934c-115">See also</span></span>

- [<span data-ttu-id="2934c-116">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="2934c-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
