---
ms.openlocfilehash: f01d0a24202ecda7e23cbe925bb6dc8962cb7574
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750720"
---
> [!CAUTION]
>  <span data-ttu-id="cff5b-101">程式碼存取安全性和部分信任的程式碼</span><span class="sxs-lookup"><span data-stu-id="cff5b-101">Code Access Security and Partially Trusted Code</span></span>  
>   
>  <span data-ttu-id="cff5b-102">.NET Framework 提供一個稱為程式碼存取安全性 (CAS) 的機制，可對在同一個應用程式中執行的不同程式碼強制執行各種信任層級。</span><span class="sxs-lookup"><span data-stu-id="cff5b-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>  <span data-ttu-id="cff5b-103">.NET Framework 中的程式碼存取安全性不應該用作一種機制，以根據程式碼來源或其他身分識別層面的來強制安全性界限。</span><span class="sxs-lookup"><span data-stu-id="cff5b-103">Code Access Security in .NET Framework should not  be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="cff5b-104">我們正在更新指南，以反映程式碼存取安全性與安全性透明的程式碼，將不會如同部分程式碼受信任的安全性界限般受到支援，特別是來源不明的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cff5b-104">We are updating our guidance to reflect that Code Access Security and Security-Transparent Code will not be supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="cff5b-105">建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。</span><span class="sxs-lookup"><span data-stu-id="cff5b-105">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>  
>   
>  <span data-ttu-id="cff5b-106">這項原則適用於所有 .NET Framework 版本，但不適用於 Silverlight 隨附的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="cff5b-106">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>