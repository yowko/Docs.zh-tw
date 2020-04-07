---
title: 雲原生應用中的身份驗證和授權
description: 為 Azure 構建雲本機 .NET 應用 |雲本機應用中的身份驗證和授權
ms.date: 03/02/2020
ms.openlocfilehash: 6261a0a72405bc1c984a04a7851aea4dd6664ddf
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805552"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>雲端原生應用程式中的驗證與授權

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

*身份驗證*是確定安全主體身份的過程。 *授權*是授予經過身份驗證的主體許可權以執行操作或訪問資源的行為。 有時身份驗證將縮短為`AuthN`,授權將縮短`AuthZ`為 。 雲原生應用程式需要依靠基於 HTTP 的開放式協議來驗證安全主體,因為用戶端和應用程式都可以在世界任何平臺或設備上運行。 唯一的常見因素是 HTTP。

許多組織仍然依賴於本地身份驗證服務,如活動目錄聯合服務 (ADFS)。 雖然這種方法傳統上為組織提供了良好的本地身份驗證需求,但雲原生應用程式受益於專為雲設計的系統。 最近 2019 年,英國國家網路安全中心 (NCSC) 的一份通報指出,「使用 Azure AD 作為主要身份驗證源的組織實際上將降低與 ADFS 相比的風險。 [此分析](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)中概述的一些原因包括:

- 訪問全套 Microsoft 認證保護技術。
- 大多數組織在某種程度上已經依賴於 Azure AD。
- NTLM 哈希的雙重哈希可確保折衷不會允許在本地活動目錄中工作的憑據。

## <a name="references"></a>參考

- [驗證基本概念](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [存取權杖與宣告](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [可能是時候放棄本地身份驗證服務了](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[前一個](identity.md)
>[下一個](azure-active-directory.md)
