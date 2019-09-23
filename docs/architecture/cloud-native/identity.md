---
title: 身分識別
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |2x2
ms.date: 09/23/2019
ms.openlocfilehash: 4cc7c04bf323d2589777df466321f6801f511b6f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183046"
---
# <a name="identity"></a>身分識別

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

大部分的軟體應用程式必須對呼叫它們的使用者或進程有一些瞭解。 與應用程式互動的使用者或進程稱為「安全性主體」，而驗證和授權這些主體的流程稱為「身分識別管理」，或簡稱「身分*識別*」。 簡單的應用程式可能會在應用程式內包含所有的身分識別管理，但這種方法並不適合許多應用程式和許多類型的安全性主體。 Windows 支援使用 Active Directory 來提供集中式驗證和授權。

<!-- (insert figure showing Windows AD auth model) -->

雖然此解決方案在公司網路內有效，但並不是專供 AD 網域外的使用者或應用程式使用。 隨著以網際網路為基礎的應用程式成長，以及雲端原生應用程式的增加，安全性模型已經進化。

在現今的雲端原生身分識別模型中，會假設架構已散發。 應用程式可以在任何地方部署，而且可能會與其他應用程式進行通訊。 用戶端可以從任何地方與這些應用程式通訊，事實上，用戶端可能是由平臺和裝置的任何組合所組成。 雲端原生身分識別解決方案會運用開放式標準，以達成用戶端安全的應用程式存取。 這些用戶端的範圍是從 Pc 或手機上的人力使用者，到在線上隨處裝載的其他應用程式，到在世界各地執行任何軟體平臺的機上盒和 IOT 裝置。

新式雲端原生身分識別解決方案通常會在判斷身分識別之後，利用安全權杖服務/伺服器（STS）發行給安全性主體的存取權杖。 存取權杖（通常是 JSON Web 權杖（JWT））包含有關安全性主體的*宣告*。 這些宣告最少會包含使用者的身分識別，但也可能包含可供應用程式用來判斷授與主體之存取層級的其他宣告。

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

通常，STS 只負責驗證主體。 判斷其對資源的存取層級，會留給應用程式的其他部分。

## <a name="references"></a>reference

- [Microsoft 身分識別平臺](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[上一頁](azure-monitor.md)
>[下一頁](authentication-authorization.md)
