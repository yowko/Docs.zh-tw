---
title: 自訂權杖處理常式
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 18be4babf7e9cfbfe9ebfb43da6f98a8544b2fe6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399973"
---
# <a name="custom-token-handlers"></a><span data-ttu-id="0dc7f-102">自訂權杖處理常式</span><span class="sxs-lookup"><span data-stu-id="0dc7f-102">Custom Token Handlers</span></span>
<span data-ttu-id="0dc7f-103">本主題討論 WIF 中的權杖處理常式以及如何使用它們來處理權杖。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="0dc7f-104">本主題也涵蓋建立權杖類型的自訂權杖處理常式所需的作業，而 WIF 中預設不支援這些權杖類型。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="0dc7f-105">WIF 中的權杖處理常式簡介</span><span class="sxs-lookup"><span data-stu-id="0dc7f-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="0dc7f-106">WIF 依賴安全性權杖處理常式來建立、讀取、寫入和驗證信賴憑證者 (RP) 應用程式或安全性權杖服務 (STS) 的權杖。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="0dc7f-107">權杖處理常式是擴充點，可讓您在 WIF 管線中新增自訂權杖處理常式，或自訂現有權杖處理常式管理權杖的方式。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="0dc7f-108">WIF 提供九個內建安全性權杖處理常式，可視需要進行修改或完全覆寫以變更功能。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="0dc7f-109">WIF 中的內建安全性權杖處理常式</span><span class="sxs-lookup"><span data-stu-id="0dc7f-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="0dc7f-110">WIF 4.5 包含衍生自抽象基底類別 <xref:System.IdentityModel.Tokens.SecurityTokenHandler> 的九個安全性權杖處理常式類別：</span><span class="sxs-lookup"><span data-stu-id="0dc7f-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="0dc7f-111">新增自訂權杖處理常式</span><span class="sxs-lookup"><span data-stu-id="0dc7f-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="0dc7f-112">部分權杖類型 (例如簡單 Web 權杖 (SWT) 和 JSON Web 權杖 (JWT)) 沒有 WIF 所提供的內建權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="0dc7f-113">針對這些權杖類型以及沒有內建處理常式的權杖類型，您需要執行下列步驟來建立自訂權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="0dc7f-114">新增自訂權杖處理常式</span><span class="sxs-lookup"><span data-stu-id="0dc7f-114">Adding a custom token handler</span></span>  
  
1.  <span data-ttu-id="0dc7f-115">建立衍生自 <xref:System.IdentityModel.Tokens.SecurityTokenHandler> 的新類別。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2.  <span data-ttu-id="0dc7f-116">覆寫下列方法，並提供您自己的實作：</span><span class="sxs-lookup"><span data-stu-id="0dc7f-116">Override the following methods and provide your own implementation:</span></span>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  <span data-ttu-id="0dc7f-117">在 *Web.config* 或 *App.config* 檔案中套用 WIF 的 **\<system.identityModel>** 區段內，新增新自訂權杖處理常式的參考。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="0dc7f-118">例如，下列組態標記會指定名為 **MyCustomTokenHandler** 且位在 **CustomToken** 命名空間中的新權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="0dc7f-119">請注意，如果您要提供自己的權杖處理常式來處理已有內建權杖處理常式的權杖類型，則需要新增 **\<remove>** 項目來捨棄預設處理常式，並改為使用自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="0dc7f-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="0dc7f-120">例如，下列組態會將預設 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 取代為自訂權杖處理常式：</span><span class="sxs-lookup"><span data-stu-id="0dc7f-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789">  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
