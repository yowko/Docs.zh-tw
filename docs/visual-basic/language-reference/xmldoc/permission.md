---
title: '&lt;權限&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 56b25955cf36598909176170235623b27da20867
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573188"
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="3839e-102">&lt;權限&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3839e-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="3839e-103">指定必要的權限的成員。</span><span class="sxs-lookup"><span data-stu-id="3839e-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3839e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3839e-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3839e-105">參數</span><span class="sxs-lookup"><span data-stu-id="3839e-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="3839e-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="3839e-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="3839e-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="3839e-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="3839e-108">括住`member`引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="3839e-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="3839e-109">成員存取權的描述。</span><span class="sxs-lookup"><span data-stu-id="3839e-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3839e-110">備註</span><span class="sxs-lookup"><span data-stu-id="3839e-110">Remarks</span></span>  
 <span data-ttu-id="3839e-111">使用`<permission>`標記來記載成員存取權。</span><span class="sxs-lookup"><span data-stu-id="3839e-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="3839e-112">使用<xref:System.Security.PermissionSet>類別，以指定成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="3839e-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="3839e-113">編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="3839e-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3839e-114">範例</span><span class="sxs-lookup"><span data-stu-id="3839e-114">Example</span></span>  
 <span data-ttu-id="3839e-115">這個範例會使用`<permission>`標記來描述所<xref:System.Security.Permissions.FileIOPermission>需要`ReadFile`方法。</span><span class="sxs-lookup"><span data-stu-id="3839e-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3839e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3839e-116">See also</span></span>
- [<span data-ttu-id="3839e-117">XML 註解標記</span><span class="sxs-lookup"><span data-stu-id="3839e-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
