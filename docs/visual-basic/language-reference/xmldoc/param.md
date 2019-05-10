---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 91489ee1664da22cc8897cdf8d12b61d962d1c83
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664201"
---
# <a name="param-visual-basic"></a><span data-ttu-id="6912b-102">\<param > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6912b-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="6912b-103">定義的參數名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="6912b-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6912b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6912b-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6912b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6912b-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6912b-106">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6912b-106">The name of a method parameter.</span></span> <span data-ttu-id="6912b-107">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="6912b-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6912b-108">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="6912b-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6912b-109">備註</span><span class="sxs-lookup"><span data-stu-id="6912b-109">Remarks</span></span>  
 <span data-ttu-id="6912b-110">`<param>`標記應該在方法宣告的註解中用來描述其中一個方法的參數。</span><span class="sxs-lookup"><span data-stu-id="6912b-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="6912b-111">文字`<param>`標籤將會出現在下列位置：</span><span class="sxs-lookup"><span data-stu-id="6912b-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="6912b-112">IntelliSense 的 參數資訊。</span><span class="sxs-lookup"><span data-stu-id="6912b-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="6912b-113">如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。</span><span class="sxs-lookup"><span data-stu-id="6912b-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="6912b-114">物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="6912b-114">Object Browser.</span></span> <span data-ttu-id="6912b-115">如需詳細資訊，請參閱[檢視程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="6912b-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="6912b-116">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="6912b-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6912b-117">範例</span><span class="sxs-lookup"><span data-stu-id="6912b-117">Example</span></span>  
 <span data-ttu-id="6912b-118">這個範例會使用`<param>`標記來描述`id`參數。</span><span class="sxs-lookup"><span data-stu-id="6912b-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6912b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6912b-119">See also</span></span>

- [<span data-ttu-id="6912b-120">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="6912b-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
