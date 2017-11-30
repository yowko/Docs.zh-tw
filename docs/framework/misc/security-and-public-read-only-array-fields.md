---
title: "安全及公開唯讀陣列欄位"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae2e9a7dd9e08344c254b52c7139c6d1dd2776a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="0e667-102">安全及公開唯讀陣列欄位</span><span class="sxs-lookup"><span data-stu-id="0e667-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="0e667-103">永遠不會使用來自 managed 程式庫公用唯讀陣列欄位來定義的邊界行為或應用程式的安全性，因為可以修改公用唯讀陣列欄位。</span><span class="sxs-lookup"><span data-stu-id="0e667-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e667-104">備註</span><span class="sxs-lookup"><span data-stu-id="0e667-104">Remarks</span></span>  
 <span data-ttu-id="0e667-105">某些.NET framework 類別包括唯讀包含平台特定界限參數的公用欄位。</span><span class="sxs-lookup"><span data-stu-id="0e667-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="0e667-106">例如，<xref:System.IO.Path.InvalidPathChars>欄位是陣列，其中描述檔案的路徑字串中不允許的字元。</span><span class="sxs-lookup"><span data-stu-id="0e667-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="0e667-107">許多類似的欄位會出現在.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="0e667-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="0e667-108">公用唯讀欄位的值要<xref:System.IO.Path.InvalidPathChars>可以修改程式碼或共用您的程式碼應用程式定義域的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e667-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="0e667-109">您不應該使用像這樣的公用唯讀陣列欄位來定義應用程式界限的行為。</span><span class="sxs-lookup"><span data-stu-id="0e667-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="0e667-110">如果您這樣做，可以變更邊界定義惡意程式碼，並使用您程式碼中非預期的方式。</span><span class="sxs-lookup"><span data-stu-id="0e667-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="0e667-111">在版本 2.0 和更新版本的.NET Framework 中，您應該使用方法的傳回新的陣列，而不是使用公用陣列欄位。</span><span class="sxs-lookup"><span data-stu-id="0e667-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="0e667-112">例如，而不是使用<xref:System.IO.Path.InvalidPathChars> 欄位中，您應該使用<xref:System.IO.Path.GetInvalidPathChars%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="0e667-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="0e667-113">請注意，.NET Framework 型別不會在內部定義界限類型使用公用欄位。</span><span class="sxs-lookup"><span data-stu-id="0e667-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="0e667-114">相反地，.NET Framework 會使用不同的私用欄位。</span><span class="sxs-lookup"><span data-stu-id="0e667-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="0e667-115">變更這些公用欄位的值不會改變行為的.NET Framework 型別。</span><span class="sxs-lookup"><span data-stu-id="0e667-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e667-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e667-116">See Also</span></span>  
 [<span data-ttu-id="0e667-117">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="0e667-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
