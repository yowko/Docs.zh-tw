---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400069"
---
# <a name="para-visual-basic"></a><span data-ttu-id="a9807-101">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9807-101">\<para> (Visual Basic)</span></span>
<span data-ttu-id="a9807-102">指定將內容格式化為段落。</span><span class="sxs-lookup"><span data-stu-id="a9807-102">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9807-103">語法</span><span class="sxs-lookup"><span data-stu-id="a9807-103">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9807-104">參數</span><span class="sxs-lookup"><span data-stu-id="a9807-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="a9807-105">段落的文字。</span><span class="sxs-lookup"><span data-stu-id="a9807-105">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9807-106">備註</span><span class="sxs-lookup"><span data-stu-id="a9807-106">Remarks</span></span>  
 <span data-ttu-id="a9807-107">`<para>`標記用於標記內（例如 [\<summary>](summary.md) 、 [\<remarks>](remarks.md) 或 [\<returns>](returns.md) ），並可讓您將結構新增至文字。</span><span class="sxs-lookup"><span data-stu-id="a9807-107">The `<para>` tag is for use inside a tag, such as [\<summary>](summary.md), [\<remarks>](remarks.md), or [\<returns>](returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="a9807-108">使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="a9807-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9807-109">範例</span><span class="sxs-lookup"><span data-stu-id="a9807-109">Example</span></span>  
 <span data-ttu-id="a9807-110">這個範例會使用 `<para>` 標記，將方法的備註區段分割 `UpdateRecord` 成兩個段落。</span><span class="sxs-lookup"><span data-stu-id="a9807-110">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a9807-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9807-111">See also</span></span>

- [<span data-ttu-id="a9807-112">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="a9807-112">XML Comment Tags</span></span>](index.md)
