---
title: "Friend 組件參考&lt;參考&gt;無效"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ae94e309ee8d18e6b5317445b7e4b7f6a42af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="b424f-102">Friend 組件參考&lt;參考&gt;無效</span><span class="sxs-lookup"><span data-stu-id="b424f-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="b424f-103">Friend 組件參考\<參考 > 無效。</span><span class="sxs-lookup"><span data-stu-id="b424f-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="b424f-104">以強式名稱簽署的組件必須在其 InternalsVisibleTo 宣告中指定公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="b424f-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="b424f-105">組件名稱傳遞給<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性建構函式識別是強式名稱組件，但它不包含`PublicKey`屬性。</span><span class="sxs-lookup"><span data-stu-id="b424f-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="b424f-106">**錯誤 ID:** BC31535</span><span class="sxs-lookup"><span data-stu-id="b424f-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b424f-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b424f-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="b424f-108">判斷公開金鑰的強式名稱的 friend 組件。</span><span class="sxs-lookup"><span data-stu-id="b424f-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="b424f-109">包含公開金鑰，因為組件名稱的一部分傳遞至<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>屬性建構函式使用`PublicKey`屬性。</span><span class="sxs-lookup"><span data-stu-id="b424f-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b424f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b424f-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="b424f-111">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="b424f-111">Friend Assemblies</span></span>](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)  
 [<span data-ttu-id="b424f-112">如何：建立簽署的 Friend 組件</span><span class="sxs-lookup"><span data-stu-id="b424f-112">How to: Create Signed Friend Assemblies</span></span>](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)
