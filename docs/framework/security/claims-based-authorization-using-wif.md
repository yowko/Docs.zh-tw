---
title: 使用 WIF 進行宣告式授權
ms.date: 03/30/2017
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
author: BrucePerlerMS
ms.openlocfilehash: 65254b31570ebf65d10c4d8c1f0fa776a6e2bae1
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48872916"
---
# <a name="claims-based-authorization-using-wif"></a>使用 WIF 進行宣告式授權
在信賴憑證者應用程式中，授權會判斷哪些是已驗證的識別可以存取的資源，以及可以針對這些資源執行哪些作業。 不適當或弱式授權會導致資訊洩露以及資料遭竄改。 本主題概述可使用 Windows Identity Foundation (WIF) 和 Security Token Service (STS) (例如 Microsoft Azure Access Control Service (ACS)) 為宣告感知 ASP.NET Web 應用程式和服務實作授權的方式。  
  
## <a name="overview"></a>總覽  
 從第一版 .NET Framework 開始，就提供了彈性的授權實作機制。 這項機制是以 **IPrincipal** 和 **IIdentity** 這兩個簡單的介面為基礎。 **IIdentity** 的具體實作表示已驗證的使用者。 例如，**WindowsIdentity** 實作表示經過 Active Directory 驗證的使用者，而 **GenericIdentity** 則表示身分識別經過自訂驗證程序驗證後的使用者。 **IPrincipal** 的具體實作可協助使用角色並根據角色存放區來檢查權限。 例如，**WindowsPrincipal** 會檢查 **WindowsIdentity** 是否擁有 Active Directory 中各群組的成員資格。 這項檢查是透過呼叫 **IPrincipal** 介面的 **IsInRole** 方法來執行。 根據角色來檢查存取權限的做法稱為角色型存取控制 (RBAC)。 如需詳細資訊，請參閱[角色型存取控制](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_1)。  宣告可用來攜帶角色相關資訊，以支援熟悉且以角色為基礎的授權機制。  
  
 此外，宣告也可以用來進行角色背後更複雜的授權決策。 宣告可以根據幾乎使用者的任何資訊：年齡、郵遞區號、鞋子尺寸等等。根據任意宣告的存取控制機制稱為宣告式授權。 如需詳細資訊，請參閱[宣告式授權](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_2)。  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a>角色型存取控制  
 RBAC 是一種授權方式，應用程式會根據使用者角色來管理和落實使用者權限。 如果使用者有執行動作所需的角色，應用程式就會授與存取權限，否則會拒絕存取。  
  
### <a name="iprincipalisinrole-method"></a>IPrincipal.IsInRole 方法  
 若要在宣告感知應用程式中實作 RBAC 這種方式，請使用 **IPrinicpal** 介面中的 **IsInRole()** 方法，就如同在非宣告感知應用程式中的做法一樣。 **IsInRole()** 方法的使用方式有下列幾種：  
  
-   明確呼叫 **IPrincipal.IsInRole("Administrator")**。 如果使用這種方式，結果會是布林值。 因此，您可以在條件陳述式中使用。 使用時，它可以位於程式碼中的任意位置。  
  
-   使用安全性要求 **PrincipalPermission.Demand()**。 使用這種方式時，如果無法滿足要求，結果會發生例外狀況。 因此，您可以在例外狀況處理策略中使用這種方式。 從效能觀點來看，擲回例外狀況與傳回布林值相比，所耗費的效能會多出許多。 使用時，它可以位於程式碼中的任意位置。  
  
-   使用宣告式屬性 **[PrincipalPermission(SecurityAction.Demand, Role = "Administrator")]**。 這種方式是用來裝飾方法，因此稱為宣告式。 它不能在方法實作內的程式碼區塊中使用。 如果無法滿足要求，結果會發生例外狀況。 因此，您應該確認可以在例外狀況處理策略中使用這種方式。  
  
-   使用 URL 授權，使用 **web.config** 中的 **\<authorization>** 區段。如果您是在 URL 層級管理授權，就很適合使用這種方式。 與先前提及的方式相比，這種方式是最粗糙的。 其優點在於我們只要變更組態檔內容即可，也就是說，我們不必編譯程式碼就可以獲得變更的好處。  
  
### <a name="expressing-roles-as-claims"></a>將角色表示為宣告  
 呼叫 **IsInRole()** 方法可以檢查目前的使用者是否具有該角色。 在宣告感知應用程式中，角色是依角色宣告類型表示，而該類型可以從權杖中取得。 角色宣告類型是使用下列 URI 來表示：  
  
 `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`
  
 下列幾種方式都可以利用角色宣告類型來增加權杖內容：  
  
-   **在權杖發行期間**。 使用者通過驗證之後，身分識別提供者 STS 或同盟提供者 (例如 Microsoft Azure Access Control Service (ACS)) 就會發行角色宣告。  
  
-   **使用 ClaimsAuthenticationManager 將任意宣告轉換為宣告角色類型**。 ClaimsAuthenticationManager 是隨附於 WIF 的元件， 可允許使用者在啟動應用程式時攔截要求，並且檢查權杖以及利用新增、變更或移除宣告來轉換權杖。 如需如何使用 ClaimsAuthenticationManager 轉換宣告的詳細資訊，請參閱[How To： 實作角色型存取控制 (RBAC) 的宣告感知 ASP.NET 應用程式使用 WIF 與 ACS 在](https://go.microsoft.com/fwlink/?LinkID=247445)。  
  
-   **使用 samlSecurityTokenRequirement 組態區段將任意宣告對應至角色類型**：這是一種宣告式做法，可以僅使用組態來轉換宣告，不必撰寫任何程式碼。  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a>宣告式授權  
 宣告式授權這種方式所遵循的邏輯是憑藉宣告中的可用資料，來決定是否要授與存取權限。 請回想 RBAC 的情況是將宣告當做角色類型宣告， 並使用角色型別宣告檢查使用者是否屬於特定角色。 下列步驟示範使用宣告式授權方式的授權決策制定流程：  
  
1.  應用程式收到必須驗證使用者才能進行的要求。  
  
2.  WIF 將使用者重新導向至其識別提供者，當使用者通過驗證之後，應用程式隨即提出要求，其中包含表示使用者的相關安全性權杖，權杖內容則包含與使用者有關的宣告。 WIF 將這些宣告與表示使用者的主體產生關聯。  
  
3.  應用程式將宣告傳遞給決策邏輯機制。 決策機制可以是記憶體內部的程式碼、Web 服務呼叫、資料庫查詢、複雜的規則引擎，或是使用 ClaimsAuthorizationManager。  
  
4.  決策機制根據宣告計算結果。  
  
5.  如果結果為 true 則授與存取權限，如果為 false 則拒絕存取。 例如，規則可能是使用者必須年滿 21 歲，並且住在華盛頓州。  
  
 如果您希望利用外部的決策邏輯來處理應用程式中的宣告式授權，<xref:System.Security.Claims.ClaimsAuthorizationManager> 就很有用。 ClaimsAuthorizationManager 是隨附於 .NET 4.5 的 WIF 元件， 可讓您擷取傳入要求並實作您選擇的邏輯，根據傳入宣告制定授權決策。 如果必須變更授權邏輯，這就變得很重要。 在這種情況下，使用 ClaimsAuthorizationManager 既不會影響應用程式的完整性，還可以降低變更結果導致應用程式錯誤的可能性。 若要深入了解如何使用 ClaimsAuthorizationManager 實作宣告型存取控制，請參閱[作法：使用 WIF 與 ACS 在宣告感知 ASP.NET 應用程式中實作宣告授權](https://go.microsoft.com/fwlink/?LinkID=247446)。
