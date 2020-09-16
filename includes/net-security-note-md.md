---
ms.openlocfilehash: 8b0edd9a49ca431355ab4f57fa041c5d1756d7eb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855658"
---
> [!CAUTION]
> <span data-ttu-id="35b1e-101">代碼啟用安全性 (CAS) 和部分信任的程式碼</span><span class="sxs-lookup"><span data-stu-id="35b1e-101">Code Access Security (CAS) and Partially Trusted Code</span></span>
>
> <span data-ttu-id="35b1e-102">.NET Framework 提供一個稱為程式碼存取安全性 (CAS) 的機制，可對在同一個應用程式中執行的不同程式碼強制執行各種信任層級。</span><span class="sxs-lookup"><span data-stu-id="35b1e-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>
>
> <span data-ttu-id="35b1e-103">**.NET Core、.NET 5 或更新版本中不支援 CAS。7.0 版以後的 c # 版本不支援 CAS。**</span><span class="sxs-lookup"><span data-stu-id="35b1e-103">**CAS is not supported in .NET Core, .NET 5, or later versions. CAS is not supported by versions of C# later than 7.0.**</span></span>
>
> <span data-ttu-id="35b1e-104">.NET Framework 中的 CAS 不應作為根據程式碼來源或其他身分識別層面來強制執行安全性界限的機制。</span><span class="sxs-lookup"><span data-stu-id="35b1e-104">CAS in .NET Framework should not be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="35b1e-105">CAS 和安全性透明程式碼不支援做為具有部分信任程式碼的安全性界限，特別是未知來源的程式碼。</span><span class="sxs-lookup"><span data-stu-id="35b1e-105">CAS and Security-Transparent Code are not supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="35b1e-106">建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。</span><span class="sxs-lookup"><span data-stu-id="35b1e-106">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>
>
> <span data-ttu-id="35b1e-107">這項原則適用於所有 .NET Framework 版本，但不適用於 Silverlight 隨附的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="35b1e-107">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
