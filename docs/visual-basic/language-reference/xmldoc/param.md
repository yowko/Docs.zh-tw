---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4405fdf2defbb27aa2146d20083fd406d1f07236
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352291"
---
# <a name="param-visual-basic"></a><span data-ttu-id="b4fd4-101">\<param > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b4fd4-101">\<param> (Visual Basic)</span></span>
<span data-ttu-id="b4fd4-102">定義參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-102">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4fd4-103">語法</span><span class="sxs-lookup"><span data-stu-id="b4fd4-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4fd4-104">參數</span><span class="sxs-lookup"><span data-stu-id="b4fd4-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b4fd4-105">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-105">The name of a method parameter.</span></span> <span data-ttu-id="b4fd4-106">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="b4fd4-107">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4fd4-108">備註</span><span class="sxs-lookup"><span data-stu-id="b4fd4-108">Remarks</span></span>  
 <span data-ttu-id="b4fd4-109">`<param>` 標記應該用於方法宣告的批註中，以描述方法的其中一個參數。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="b4fd4-110">`<param>` 標記的文字會出現在下列位置：</span><span class="sxs-lookup"><span data-stu-id="b4fd4-110">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="b4fd4-111">IntelliSense 的參數資訊。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-111">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="b4fd4-112">如需詳細資訊，請參閱 [Using IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="b4fd4-113">物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-113">Object Browser.</span></span> <span data-ttu-id="b4fd4-114">如需詳細資訊，請參閱[檢視程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="b4fd4-115">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-115">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4fd4-116">範例</span><span class="sxs-lookup"><span data-stu-id="b4fd4-116">Example</span></span>  
 <span data-ttu-id="b4fd4-117">這個範例會使用 `<param>` 標記來描述 `id` 參數。</span><span class="sxs-lookup"><span data-stu-id="b4fd4-117">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b4fd4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4fd4-118">See also</span></span>

- [<span data-ttu-id="b4fd4-119">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="b4fd4-119">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
