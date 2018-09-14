---
title: Principal 和 Identity 物件
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET Framework], identity objects
- principal objects, about principal objects
- security [.NET Framework], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8c7616a3187cd5fa28f231dffd15b0bfeea4b7f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519717"
---
# <a name="principal-and-identity-objects"></a>Principal 和 Identity 物件
Managed 程式碼可以探索的身分識別或透過主體的角色<xref:System.Security.Principal.IPrincipal>物件，其中包含的參考<xref:System.Security.Principal.IIdentity>物件。 它可能有助於您比較 Identity 和 Principal 物件，以熟悉例如使用者和群組帳戶的概念。 在大部分網路環境中，使用者帳戶代表人員或程式，而群組帳戶代表特定類別的使用者和他們擁有的權限。 同樣地，.NET Framework Identity 物件代表使用者，而角色代表成員資格和安全性內容。 在 .NET Framework 中，Principal 物件會封裝身分識別物件和角色。 .NET framework 應用程式會根據主體的身分識別或更常見的是其角色成員資格，授與主體權限。  
  
## <a name="identity-objects"></a>Identity 物件  
 Identity 物件會封裝已驗證的使用者或實體相關資訊。 在其最基本層級中，Identity 物件會包含名稱和驗證類型。 名稱可以是使用者的名稱或 Windows 帳戶的名稱，而驗證類型可以是支援的登入通訊協定，例如 Kerberos V5 或自訂值。 .NET Framework 會定義<xref:System.Security.Principal.GenericIdentity>物件，可以用於大部分的自訂登入案例和更特製化<xref:System.Security.Principal.WindowsIdentity>可在您想要您的應用程式依賴 Windows 驗證的物件。 此外，您可以定義自己的身分識別類別，它會封裝自訂使用者資訊。  
  
 <xref:System.Security.Principal.IIdentity>介面定義屬性來存取名稱和驗證類型，例如 Kerberos V5 或 NTLM。 所有**身分識別**類別會實作 **IIdentity** 介面。 **Identity** 物件和 Windows NT 處理序語彙基元 (執行緒目前在其底下執行) 之間沒有任何必要的關聯性。 不過，如果 **Identity** 物件是 **WindowsIdentity** 物件時，身分識別會假設為代表 Windows NT 安全性語彙基元。  
  
## <a name="principal-objects"></a>Principal 物件  
 Principal 物件代表執行程式碼所在的安全性內容。 實作以角色為基礎的安全性之應用程式，會根據與 Principal 物件相關聯的角色授與權限。 類似於 identity 物件，.NET Framework 會提供<xref:System.Security.Principal.GenericPrincipal>物件和<xref:System.Security.Principal.WindowsPrincipal>物件。 您也可以定義自己的自訂主體類別。  
  
 <xref:System.Security.Principal.IPrincipal>介面會定義屬性，以存取相關聯**身分識別**物件的方法來判斷使用者是否由識別**主體**物件是的成員指定的角色。 所有 **Principal** 類別會實作 **IPrincipal** 介面以及任何其他需要的屬性和方法。 例如，通用語言執行平台提供 **WindowsPrincipal** 類別，實作其他功能以將 Windows NT 或 Windows 2000 群組成員資格對應至角色。  
  
 A**主體**物件所繫結至呼叫內容 (<xref:System.Runtime.Remoting.Messaging.CallContext>) 應用程式定義域中的物件 (<xref:System.AppDomain>)。 預設呼叫內容一律使用每個新的 **AppDomain** 建立，因此永遠有呼叫內容可以接受 **Principal** 物件。 建立新的執行緒時，也會針對執行緒建立 **CallContext** 物件。 **Principal** 物件參考會自動從建立的執行緒複製到新執行緒的 **CallContext**。 如果執行階段無法判斷哪個 **Principal** 物件屬於執行緒的建立者，它會依照 **Principal** 和 **Identity** 物件建立的預設原則。  
  
 可設定的應用程式定義域特定原則會定義規則，來決定哪種類型的 **Principal** 物件與新的應用程式定義域相關聯。 安全性原則允許時，執行階段可以建立 **Principal** 和 **Identity** 物件，反映與目前執行緒相關聯的作業系統語彙基元。 根據預設，執行階段會使用 **Principal** 和 **Identity** 物件，代表未經授權的使用者。 執行階段不會建立這些預設 **Principal** 和 **Identity** 物件，直到程式碼嘗試存取它們為止。  
  
 會建立應用程式定義域之信任的程式碼，可以設定應用程式定義域原則，控制預設 **Principal** 和 **Identity** 物件的建構。 此應用程式定義域專屬的原則適用於所有應用程式定義域中的執行緒。 未受管理、 受信任主機本來就具有能夠設定此原則，但必須設定此原則的 managed 程式碼<xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>以控制定義域原則。  
  
 跨應用程式定義域但是在相同處理序內傳輸 **Principal** 物件時 (因此是在同一部電腦上)，遠端基礎結構會將參考複製到 **Principal** 物件，該物件將呼叫者的內容與被呼叫端的內容產生關聯。  
  
## <a name="see-also"></a>另請參閱

- [操作說明：建立 WindowsPrincipal 物件](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)  
- [操作說明：建立 GenericPrincipal 和 GenericIdentity 物件](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)  
- [取代 Principal 物件](../../../docs/standard/security/replacing-a-principal-object.md)  
- [模擬和還原](../../../docs/standard/security/impersonating-and-reverting.md)  
- [以角色為基礎的安全性](../../../docs/standard/security/role-based-security.md)  
- [重要的安全性概念](../../../docs/standard/security/key-security-concepts.md)
