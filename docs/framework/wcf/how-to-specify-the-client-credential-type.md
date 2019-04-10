---
title: HOW TO：指定用戶端認證類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: 775c6a297047c7a0e16db091f9a22686fdb01efb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339394"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="52164-102">HOW TO：指定用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="52164-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="52164-103">在設定過安全性模式 (傳輸或訊息) 後，您就會擁有設定用戶端認證類型的選項。</span><span class="sxs-lookup"><span data-stu-id="52164-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="52164-104">這個屬性會指定用戶端必須提供給服務以進行驗證的認證類型。</span><span class="sxs-lookup"><span data-stu-id="52164-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="52164-105">如需有關如何設定安全性模式 （在設定用戶端認證類型之前的必要步驟） 的詳細資訊，請參閱[How to:設定安全性模式](../../../docs/framework/wcf/how-to-set-the-security-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="52164-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="52164-106">透過程式碼設定用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="52164-106">To set the client credential type in code</span></span>  
  
1. <span data-ttu-id="52164-107">建立服務將會使用之繫結的執行個體。</span><span class="sxs-lookup"><span data-stu-id="52164-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="52164-108">這個範例會使用 <xref:System.ServiceModel.WSHttpBinding> 繫結。</span><span class="sxs-lookup"><span data-stu-id="52164-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2. <span data-ttu-id="52164-109">將 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="52164-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="52164-110">這個範例會使用訊息模式。</span><span class="sxs-lookup"><span data-stu-id="52164-110">This example uses the Message mode.</span></span>  
  
3. <span data-ttu-id="52164-111">將 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="52164-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="52164-112">這個範例會將該屬性設定為使用 Windows 驗證 (<xref:System.ServiceModel.MessageCredentialType.Windows>)。</span><span class="sxs-lookup"><span data-stu-id="52164-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="52164-113">透過組態設定用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="52164-113">To set the client credential type in configuration</span></span>  
  
1. <span data-ttu-id="52164-114">新增[ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)至組態檔的項目。</span><span class="sxs-lookup"><span data-stu-id="52164-114">Add a [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2. <span data-ttu-id="52164-115">做為子項目中，新增[\<繫結 >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)項目。</span><span class="sxs-lookup"><span data-stu-id="52164-115">As a child element, add a [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3. <span data-ttu-id="52164-116">新增適當的繫結。</span><span class="sxs-lookup"><span data-stu-id="52164-116">Add an appropriate binding.</span></span> <span data-ttu-id="52164-117">這個範例會使用[ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="52164-117">This example uses the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4. <span data-ttu-id="52164-118">新增[\<繫結 >](../../../docs/framework/misc/binding.md)項目並將`name`屬性設為適當的值。</span><span class="sxs-lookup"><span data-stu-id="52164-118">Add a [\<binding>](../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="52164-119">這個範例會使用 "SecureBinding" 的名稱。</span><span class="sxs-lookup"><span data-stu-id="52164-119">This example uses the name "SecureBinding".</span></span>  
  
5. <span data-ttu-id="52164-120">新增 `<security>` 繫結。</span><span class="sxs-lookup"><span data-stu-id="52164-120">Add a `<security>` binding.</span></span> <span data-ttu-id="52164-121">將 `mode` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="52164-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="52164-122">這個範例會將其設定為 `"Message"`。</span><span class="sxs-lookup"><span data-stu-id="52164-122">This example sets it to `"Message"`.</span></span>  
  
6. <span data-ttu-id="52164-123">根據安全性模式，新增 `<message>` 或 `<transport>` 項目。</span><span class="sxs-lookup"><span data-stu-id="52164-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="52164-124">將 `clientCredentialType` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="52164-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="52164-125">這個範例會使用 `"Windows"`。</span><span class="sxs-lookup"><span data-stu-id="52164-125">This example uses `"Windows"`.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="52164-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52164-126">See also</span></span>

- [<span data-ttu-id="52164-127">保護服務的安全</span><span class="sxs-lookup"><span data-stu-id="52164-127">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="52164-128">HOW TO：設定安全性模式</span><span class="sxs-lookup"><span data-stu-id="52164-128">How to: Set the Security Mode</span></span>](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
