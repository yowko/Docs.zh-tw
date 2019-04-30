---
ms.openlocfilehash: f01d0a24202ecda7e23cbe925bb6dc8962cb7574
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750720"
---
> [!CAUTION]
>  程式碼存取安全性和部分信任的程式碼  
>   
>  .NET Framework 提供一個稱為程式碼存取安全性 (CAS) 的機制，可對在同一個應用程式中執行的不同程式碼強制執行各種信任層級。  .NET Framework 中的程式碼存取安全性不應該用作一種機制，以根據程式碼來源或其他身分識別層面的來強制安全性界限。 我們正在更新指南，以反映程式碼存取安全性與安全性透明的程式碼，將不會如同部分程式碼受信任的安全性界限般受到支援，特別是來源不明的程式碼。 建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。  
>   
>  這項原則適用於所有 .NET Framework 版本，但不適用於 Silverlight 隨附的 .NET Framework。