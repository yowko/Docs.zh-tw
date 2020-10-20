---
ms.openlocfilehash: 3164233f1ac056de385faa119143d75d3c2dc50c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224343"
---
> [!CAUTION]
> 代碼啟用安全性 (CAS) 和部分信任的程式碼
>
> .NET Framework 提供一個稱為程式碼存取安全性 (CAS) 的機制，可對在同一個應用程式中執行的不同程式碼強制執行各種信任層級。
>
> **.NET Core、.NET 5 或更新版本中不支援 CAS。7.0 版以後的 c # 版本不支援 CAS。**
>
> .NET Framework 中的 CAS 不應作為根據程式碼來源或其他身分識別層面來強制執行安全性界限的機制。 CAS 和 Security-Transparent 程式碼不支援做為具有部分信任程式碼的安全性界限，特別是未知來源的程式碼。 建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。 .NET Framework 不會針對可能針對 CAS 沙箱探索的任何權限提高攻擊，發出安全性修補程式。
>
> 這項原則適用於所有 .NET Framework 版本，但不適用於 Silverlight 隨附的 .NET Framework。
