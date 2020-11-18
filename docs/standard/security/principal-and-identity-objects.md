---
title: Principal 和 Identity 物件
description: 閱讀代表 .NET 中使用者的身分識別物件。 另請參閱主要物件，其會將身分識別物件封裝 & 角色。
ms.date: 07/15/2020
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET], identity objects
- principal objects, about principal objects
- security [.NET], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
ms.openlocfilehash: cfda506fc29e9a86e97b3c99faf2d4155c894f03
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824235"
---
# <a name="principal-and-identity-objects"></a>Principal 和 Identity 物件

> [!NOTE]
> 本文適用于 Windows。
>
> 如需 ASP.NET Core 的詳細資訊，請參閱 [ASP.NET Core 安全性](/aspnet/core/security/)。

Managed 程式碼可以透過 <xref:System.Security.Principal.IPrincipal> 包含物件參考的物件，探索主體的身分識別或角色 <xref:System.Security.Principal.IIdentity> 。 它可能有助於您比較 Identity 和 Principal 物件，以熟悉例如使用者和群組帳戶的概念。 在大部分網路環境中，使用者帳戶代表人員或程式，而群組帳戶代表特定類別的使用者和他們擁有的權限。 同樣地，.NET identity 物件代表使用者，而角色則代表成員資格和安全性內容。 在 .NET 中，主體物件會封裝身分識別物件和角色。 .NET 應用程式會根據主體的身分識別或更常見的角色成員資格，授與主體許可權。  
  
## <a name="identity-objects"></a>Identity 物件

Identity 物件會封裝已驗證的使用者或實體相關資訊。 在其最基本層級中，Identity 物件會包含名稱和驗證類型。 名稱可以是使用者的名稱或 Windows 帳戶的名稱，而驗證類型可以是支援的登入通訊協定，例如 Kerberos V5 或自訂值。 .NET 會定義一個 <xref:System.Security.Principal.GenericIdentity> 物件，可用於大部分的自訂登入案例，以及 <xref:System.Security.Principal.WindowsIdentity> 當您想要讓應用程式依賴 Windows 驗證時，可使用更特製化的物件。 此外，您可以定義自己的身分識別類別，它會封裝自訂使用者資訊。  
  
<xref:System.Security.Principal.IIdentity>介面會定義用來存取名稱和驗證類型（例如 Kerberos V5 或 NTLM）的屬性。 所有 **身分識別** 類別會實作 **IIdentity** 介面。 **Identity** 物件和 Windows NT 處理序語彙基元 (執行緒目前在其底下執行) 之間沒有任何必要的關聯性。 不過，如果 **Identity** 物件是 **WindowsIdentity** 物件時，身分識別會假設為代表 Windows NT 安全性語彙基元。  
  
## <a name="principal-objects"></a>Principal 物件

Principal 物件代表執行程式碼所在的安全性內容。 實作以角色為基礎的安全性之應用程式，會根據與 Principal 物件相關聯的角色授與權限。 與 identity 物件類似，.NET 提供了 <xref:System.Security.Principal.GenericPrincipal> 物件和 <xref:System.Security.Principal.WindowsPrincipal> 物件。 您也可以定義自己的自訂主體類別。  
  
<xref:System.Security.Principal.IPrincipal>介面會定義用來存取相關聯身分 **識別** 物件的屬性，以及用來判斷 **主體** 物件所識別的使用者是否為指定角色成員的方法。 所有 **Principal** 類別會實作 **IPrincipal** 介面以及任何其他需要的屬性和方法。 例如，通用語言執行平台提供 **WindowsPrincipal** 類別，實作其他功能以將 Windows NT 或 Windows 2000 群組成員資格對應至角色。  
  
**主體** 物件會系結至 <xref:System.Runtime.Remoting.Messaging.CallContext> 應用程式域中的呼叫內容 () 物件 (<xref:System.AppDomain>) 。 預設呼叫內容一律使用每個新的 **AppDomain** 建立，因此永遠有呼叫內容可以接受 **Principal** 物件。 建立新的執行緒時，也會針對執行緒建立 **CallContext** 物件。 **Principal** 物件參考會自動從建立的執行緒複製到新執行緒的 **CallContext**。 如果執行階段無法判斷哪個 **Principal** 物件屬於執行緒的建立者，它會依照 **Principal** 和 **Identity** 物件建立的預設原則。  
  
可設定的應用程式定義域特定原則會定義規則，來決定哪種類型的 **Principal** 物件與新的應用程式定義域相關聯。 安全性原則允許時，執行階段可以建立 **Principal** 和 **Identity** 物件，反映與目前執行緒相關聯的作業系統語彙基元。 根據預設，執行階段會使用 **Principal** 和 **Identity** 物件，代表未經授權的使用者。 執行階段不會建立這些預設 **Principal** 和 **Identity** 物件，直到程式碼嘗試存取它們為止。  
  
會建立應用程式定義域之信任的程式碼，可以設定應用程式定義域原則，控制預設 **Principal** 和 **Identity** 物件的建構。 此應用程式定義域專屬的原則適用於所有應用程式定義域中的執行緒。 非受控、受信任的主機原本就可以設定此原則，但設定此原則的 managed 程式碼必須具有 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> 控制網域原則的。  
  
跨應用程式定義域但是在相同處理序內傳輸 **Principal** 物件時 (因此是在同一部電腦上)，遠端基礎結構會將參考複製到 **Principal** 物件，該物件將呼叫者的內容與被呼叫端的內容產生關聯。  
  
## <a name="see-also"></a>請參閱

- [作法：建立 WindowsPrincipal 物件](how-to-create-a-windowsprincipal-object.md)
- [作法：建立 GenericPrincipal 和 GenericIdentity 物件](how-to-create-genericprincipal-and-genericidentity-objects.md)
- [取代 Principal 物件](replacing-a-principal-object.md)
- [模擬和還原](impersonating-and-reverting.md)
- [以角色為基礎的安全性](role-based-security.md)
- [重要的安全性概念](key-security-concepts.md)
- [ASP.NET Core 安全性](/aspnet/core/security/)
