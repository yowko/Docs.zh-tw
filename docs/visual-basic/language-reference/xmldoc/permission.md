---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: ae6167f3582fe22cd10d9ef7a10873d6d9bdfa06
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872554"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="a4713-101">\<permission> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4713-101">\<permission> (Visual Basic)</span></span>

<span data-ttu-id="a4713-102">指定成員的必要許可權。</span><span class="sxs-lookup"><span data-stu-id="a4713-102">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4713-103">語法</span><span class="sxs-lookup"><span data-stu-id="a4713-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4713-104">參數</span><span class="sxs-lookup"><span data-stu-id="a4713-104">Parameters</span></span>  

 `member`  
 <span data-ttu-id="a4713-105">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="a4713-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a4713-106">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="a4713-106">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="a4713-107">`member`以引號括住 ( "" ) 。</span><span class="sxs-lookup"><span data-stu-id="a4713-107">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="a4713-108">成員存取權的描述。</span><span class="sxs-lookup"><span data-stu-id="a4713-108">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4713-109">備註</span><span class="sxs-lookup"><span data-stu-id="a4713-109">Remarks</span></span>  

 <span data-ttu-id="a4713-110">使用 `<permission>` 標記來記錄成員的存取。</span><span class="sxs-lookup"><span data-stu-id="a4713-110">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="a4713-111">使用 <xref:System.Security.PermissionSet> 類別來指定成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="a4713-111">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="a4713-112">使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。</span><span class="sxs-lookup"><span data-stu-id="a4713-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4713-113">範例</span><span class="sxs-lookup"><span data-stu-id="a4713-113">Example</span></span>  

 <span data-ttu-id="a4713-114">這個範例會使用 `<permission>` 標記來描述 <xref:System.Security.Permissions.FileIOPermission> 方法所需的 `ReadFile` 。</span><span class="sxs-lookup"><span data-stu-id="a4713-114">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="a4713-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4713-115">See also</span></span>

- [<span data-ttu-id="a4713-116">XML 註解標籤</span><span class="sxs-lookup"><span data-stu-id="a4713-116">XML Comment Tags</span></span>](index.md)
