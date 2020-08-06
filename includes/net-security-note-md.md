---
ms.openlocfilehash: 8b0edd9a49ca431355ab4f57fa041c5d1756d7eb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855658"
---
> [!CAUTION]
>  (CA) 和部分信任程式碼的代碼啟用安全性
>
> .NET Framework 提供一個稱為程式碼存取安全性 (CAS) 的機制，可對在同一個應用程式中執行的不同程式碼強制執行各種信任層級。
>
> **在 .NET Core、.NET 5 或更新版本中不支援 CAS。7.0 以後的 c # 版本不支援 CAS。**
>
> .NET Framework 中的 CAS 不應作為根據程式碼來源或其他身分識別層面來強制安全性界限的機制。 不支援 CAS 和安全性透明的程式碼作為具有部分信任程式碼的安全性界限，特別是未知來源的程式碼。 建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。
>
> 這項原則適用於所有 .NET Framework 版本，但不適用於 Silverlight 隨附的 .NET Framework。
