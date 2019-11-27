---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 62f70ae7f40fa3cde9492563b7bd14dfa5940a5f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352235"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="3ecf4-101">\<會傳回 > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="3ecf4-101">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="3ecf4-102">指定屬性或函數的傳回值。</span><span class="sxs-lookup"><span data-stu-id="3ecf4-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ecf4-103">語法</span><span class="sxs-lookup"><span data-stu-id="3ecf4-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ecf4-104">參數</span><span class="sxs-lookup"><span data-stu-id="3ecf4-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="3ecf4-105">傳回值的描述。</span><span class="sxs-lookup"><span data-stu-id="3ecf4-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ecf4-106">備註</span><span class="sxs-lookup"><span data-stu-id="3ecf4-106">Remarks</span></span>  
 <span data-ttu-id="3ecf4-107">在方法宣告的批註中使用 `<returns>` 標記，以描述傳回值。</span><span class="sxs-lookup"><span data-stu-id="3ecf4-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="3ecf4-108">使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="3ecf4-108">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ecf4-109">範例</span><span class="sxs-lookup"><span data-stu-id="3ecf4-109">Example</span></span>  
 <span data-ttu-id="3ecf4-110">這個範例會使用 `<returns>` 標記來說明 `DoesRecordExist` 函數傳回的內容。</span><span class="sxs-lookup"><span data-stu-id="3ecf4-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3ecf4-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ecf4-111">See also</span></span>

- [<span data-ttu-id="3ecf4-112">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="3ecf4-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
