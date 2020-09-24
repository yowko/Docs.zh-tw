---
title: 身分識別
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |身份
ms.date: 05/13/2020
ms.openlocfilehash: 66ff29947093d7c4fe57b11039190836dc37db08
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163748"
---
# <a name="identity"></a>身分識別

大部分的軟體應用程式都必須知道呼叫它們的使用者或進程。 與應用程式互動的使用者或進程稱為安全性主體，而驗證和授權這些主體的程式稱為身分識別管理或單純身分 *識別*。 簡單的應用程式可能會在應用程式中包含所有的身分識別管理，但這種方法並不適合許多應用程式和許多類型的安全性主體。 Windows 支援使用 Active Directory 來提供集中式驗證和授權。

<!-- (insert figure showing Windows AD auth model) -->

雖然此解決方案在公司網路中是有效的，但它並不是專為 AD 網域以外的使用者或應用程式所使用而設計。 隨著以網際網路為基礎的應用程式成長和雲端原生應用程式的成長，安全性模型也已演進。

在現今的雲端原生身分識別模型中，架構會假設為已散發。 應用程式可以在任何地方部署，並可在任何地方與其他應用程式通訊。 用戶端可能會從任何地方與這些應用程式通訊，事實上，用戶端可能包含平臺和裝置的任何組合。 雲端原生身分識別解決方案利用開放式標準，從用戶端達成安全的應用程式存取。 這些用戶端的範圍是從電腦或手機上的使用者，到線上裝載的其他應用程式，到在世界各地執行任何軟體平臺的機上盒和 IOT 裝置。

新式的雲端原生身分識別解決方案通常會利用安全權杖服務/伺服器 (STS) 的存取權杖，在判斷身分識別之後，將其授與安全性主體。 存取權杖（通常是 (JWT) 的 JSON Web 權杖）包含有關安全性主體的 *宣告* 。 這些宣告最少包含使用者的身分識別，但也可能包含其他宣告，可供應用程式用來判斷授與主體的存取層級。

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

通常，STS 只負責驗證主體。 判斷其對資源的存取層級會保留給應用程式的其他部分。

## <a name="references"></a>參考資料

- [Microsoft 身分識別平台](/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[上一個](azure-monitor.md) 
>[下一步](authentication-authorization.md)
