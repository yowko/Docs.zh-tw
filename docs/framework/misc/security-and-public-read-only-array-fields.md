---
title: 安全及公開唯讀陣列欄位
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d36009fa4fc7b9299708768fe34a75f1fde6797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910730"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="65674-102">安全及公開唯讀陣列欄位</span><span class="sxs-lookup"><span data-stu-id="65674-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="65674-103">絕對不要使用受控程式庫中的唯讀公用陣列欄位來定義應用程式的界限行為或安全性, 因為可以修改唯讀的公用陣列欄位。</span><span class="sxs-lookup"><span data-stu-id="65674-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65674-104">備註</span><span class="sxs-lookup"><span data-stu-id="65674-104">Remarks</span></span>  
 <span data-ttu-id="65674-105">某些 .NET framework 類別包含唯讀公用欄位, 其中包含平臺特定的界限參數。</span><span class="sxs-lookup"><span data-stu-id="65674-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="65674-106">例如, <xref:System.IO.Path.InvalidPathChars>欄位是描述檔案路徑字串中不允許之字元的陣列。</span><span class="sxs-lookup"><span data-stu-id="65674-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="65674-107">許多類似的欄位都會出現在 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="65674-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="65674-108">公用唯讀欄位 (例如<xref:System.IO.Path.InvalidPathChars> ) 的值可以由您的程式碼或共用您程式碼應用程式域的程式碼修改。</span><span class="sxs-lookup"><span data-stu-id="65674-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="65674-109">您不應該使用唯讀公用陣列欄位, 如下所示來定義應用程式的界限行為。</span><span class="sxs-lookup"><span data-stu-id="65674-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="65674-110">如果您這樣做, 惡意程式碼可以改變界限定義, 並以非預期的方式使用您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="65674-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="65674-111">在2.0 版和更新版本的 .NET Framework 中, 您應該使用傳回新陣列的方法, 而不是使用公用陣列欄位。</span><span class="sxs-lookup"><span data-stu-id="65674-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="65674-112">例如, 您應該<xref:System.IO.Path.InvalidPathChars> <xref:System.IO.Path.GetInvalidPathChars%2A>使用方法, 而不是使用欄位。</span><span class="sxs-lookup"><span data-stu-id="65674-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="65674-113">請注意, .NET Framework 類型不會使用公用欄位在內部定義界限類型。</span><span class="sxs-lookup"><span data-stu-id="65674-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="65674-114">相反地, .NET Framework 會使用個別的私用欄位。</span><span class="sxs-lookup"><span data-stu-id="65674-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="65674-115">變更這些公用欄位的值並不會改變 .NET Framework 類型的行為。</span><span class="sxs-lookup"><span data-stu-id="65674-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65674-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65674-116">See also</span></span>

- [<span data-ttu-id="65674-117">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="65674-117">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
