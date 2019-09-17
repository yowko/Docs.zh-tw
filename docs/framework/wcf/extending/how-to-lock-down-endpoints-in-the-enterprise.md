---
title: HOW TO：鎖定企業的端點
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: fb9232c98f672701c60fa9228bb34d7b24d52330
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796973"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a><span data-ttu-id="8d511-102">作法：鎖定企業的端點</span><span class="sxs-lookup"><span data-stu-id="8d511-102">How to: Lock Down Endpoints in the Enterprise</span></span>

<span data-ttu-id="8d511-103">大型企業通常需要在遵循企業安全性原則的環境中開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d511-103">Large enterprises often require that applications are developed in compliance with enterprise security policies.</span></span> <span data-ttu-id="8d511-104">下列主題討論如何開發和安裝用戶端端點驗證程式，可用來驗證電腦上安裝的所有 Windows Communication Foundation （WCF）用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d511-104">The following topic discusses how to develop and install a client endpoint validator that can be used to validate all Windows Communication Foundation (WCF) client applications installed on computers.</span></span>

<span data-ttu-id="8d511-105">在此情況下，驗證程式是一種用戶端驗證器，因為這個端點行為會加入至 machine.config 檔案中的用戶端[ \<s >](../../configure-apps/file-schema/wcf/commonbehaviors.md)區段。</span><span class="sxs-lookup"><span data-stu-id="8d511-105">In this case, the validator is a client validator because this endpoint behavior is added to the client [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section in the machine.config file.</span></span> <span data-ttu-id="8d511-106">WCF 只會載入用戶端應用程式的一般端點行為，並且只會針對服務應用程式載入泛型服務行為。</span><span class="sxs-lookup"><span data-stu-id="8d511-106">WCF loads common endpoint behaviors only for client applications and loads common service behaviors only for service applications.</span></span> <span data-ttu-id="8d511-107">若要為服務應用程式安裝這個相同的驗證器，驗證器必須是服務行為。</span><span class="sxs-lookup"><span data-stu-id="8d511-107">To install this same validator for service applications, the validator must be a service behavior.</span></span> <span data-ttu-id="8d511-108">如需詳細資訊，請參閱[ \<s >](../../configure-apps/file-schema/wcf/commonbehaviors.md)一節。</span><span class="sxs-lookup"><span data-stu-id="8d511-108">For more information, see the [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d511-109">當應用程式在部分信任環境中<xref:System.Security.AllowPartiallyTrustedCallersAttribute>執行時，未以屬性（APTCA）標記的服務或端點行為（已新增至設定檔的[ \<s >](../../configure-apps/file-schema/wcf/commonbehaviors.md)區段）不會執行，而且不會發生這種情況時，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8d511-109">Service or endpoint behaviors not marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute (APTCA) that are added to the [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section of a configuration file are not run when the application runs in a partial trust environment, and no exception is thrown when this occurs.</span></span> <span data-ttu-id="8d511-110">若要強制執行通用行為 (例如驗證器)，您必須執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="8d511-110">To enforce the running of common behaviors such as validators, you must either:</span></span>
>
> - <span data-ttu-id="8d511-111">以<xref:System.Security.AllowPartiallyTrustedCallersAttribute>屬性標示您的一般行為，讓它可以在部署為部分信任的應用程式時執行。</span><span class="sxs-lookup"><span data-stu-id="8d511-111">Mark your common behavior with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute so that it can run when deployed as a Partial Trust application.</span></span> <span data-ttu-id="8d511-112">請注意，您可以在電腦上設定登錄項目，以防止已標記 APTCA 的組件執行。</span><span class="sxs-lookup"><span data-stu-id="8d511-112">Note that a registry entry can be set on the computer to prevent APTCA-marked assemblies from running..</span></span>
>
> - <span data-ttu-id="8d511-113">請確定應用程式是否部署為完全信任的應用程式，使用者無法修改代碼啟用安全性設定以在部分信任環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d511-113">Ensure that if the application is deployed as a fully-trusted application that users cannot modify the code-access security settings to run the application in a Partial Trust environment.</span></span> <span data-ttu-id="8d511-114">如果可以執行這項操作，自訂驗證器就不會執行，也不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8d511-114">If they can do so, the custom validator does not run and no exception is thrown.</span></span> <span data-ttu-id="8d511-115">如需確保這項工作的其中一`levelfinal`種方式，請參閱使用[代碼啟用安全性原則工具（caspol.exe）](https://go.microsoft.com/fwlink/?LinkId=248222)的選項。</span><span class="sxs-lookup"><span data-stu-id="8d511-115">For one way to ensure this, see the `levelfinal` option using [Code Access Security Policy Tool (Caspol.exe)](https://go.microsoft.com/fwlink/?LinkId=248222).</span></span>
>
> <span data-ttu-id="8d511-116">如需詳細資訊，請參閱[部分信任最佳做法](../feature-details/partial-trust-best-practices.md)和[支援的部署案例](../feature-details/supported-deployment-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="8d511-116">For more information, see [Partial Trust Best Practices](../feature-details/partial-trust-best-practices.md) and [Supported Deployment Scenarios](../feature-details/supported-deployment-scenarios.md).</span></span>

### <a name="to-create-the-endpoint-validator"></a><span data-ttu-id="8d511-117">若要建立端點驗證器</span><span class="sxs-lookup"><span data-stu-id="8d511-117">To create the endpoint validator</span></span>

1. <span data-ttu-id="8d511-118">以 <xref:System.ServiceModel.Description.IEndpointBehavior> 方法中所需的驗證步驟建立 <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A>。</span><span class="sxs-lookup"><span data-stu-id="8d511-118">Create an <xref:System.ServiceModel.Description.IEndpointBehavior> with the desired validation steps in the <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> method.</span></span> <span data-ttu-id="8d511-119">下列程式碼提供一個範例。</span><span class="sxs-lookup"><span data-stu-id="8d511-119">The following code provides an example.</span></span> <span data-ttu-id="8d511-120">（`InternetClientValidatorBehavior` 取自[安全性驗證](../samples/security-validation.md)範例。）</span><span class="sxs-lookup"><span data-stu-id="8d511-120">(The `InternetClientValidatorBehavior` is taken from the [Security Validation](../samples/security-validation.md) sample.)</span></span>

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. <span data-ttu-id="8d511-121">建立新的 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>，它會註冊步驟 1 中建立的端點驗證器。</span><span class="sxs-lookup"><span data-stu-id="8d511-121">Create new <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that registers the endpoint validator created in step 1.</span></span> <span data-ttu-id="8d511-122">下列程式碼範例會顯示這點。</span><span class="sxs-lookup"><span data-stu-id="8d511-122">The following code example shows this.</span></span> <span data-ttu-id="8d511-123">（此範例的原始程式碼位於[安全性驗證](../samples/security-validation.md)範例中）。</span><span class="sxs-lookup"><span data-stu-id="8d511-123">(The original code for this example is in the [Security Validation](../samples/security-validation.md) sample.)</span></span>

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. <span data-ttu-id="8d511-124">請務必以強式名稱簽署編譯的組件。</span><span class="sxs-lookup"><span data-stu-id="8d511-124">Make sure the compiled assembly is signed with a strong name.</span></span> <span data-ttu-id="8d511-125">如需詳細資訊，請參閱[強式名稱工具（sn.exe）。EXE）](https://go.microsoft.com/fwlink/?LinkId=248217)和適用于您語言的編譯器命令。</span><span class="sxs-lookup"><span data-stu-id="8d511-125">For details, see the [Strong Name Tool (SN.EXE)](https://go.microsoft.com/fwlink/?LinkId=248217) and the compiler commands for your language.</span></span>

### <a name="to-install-the-validator-into-the-target-computer"></a><span data-ttu-id="8d511-126">若要將驗證器安裝至目標電腦</span><span class="sxs-lookup"><span data-stu-id="8d511-126">To install the validator into the target computer</span></span>

1. <span data-ttu-id="8d511-127">使用適當的機制安裝端點驗證器。</span><span class="sxs-lookup"><span data-stu-id="8d511-127">Install the endpoint validator using the appropriate mechanism.</span></span> <span data-ttu-id="8d511-128">在企業中，您可以使用群組原則和 Systems Management Server (SMS) 安裝端點驗證器。</span><span class="sxs-lookup"><span data-stu-id="8d511-128">In an enterprise, this can be using Group Policy and Systems Management Server (SMS).</span></span>

2. <span data-ttu-id="8d511-129">使用[Gacutil （全域組件快取工具）](../../tools/gacutil-exe-gac-tool.md)，將強式名稱的元件安裝到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="8d511-129">Install the strongly-named assembly into the global assembly cache using the [Gacutil.exe (Global Assembly Cache Tool)](../../tools/gacutil-exe-gac-tool.md).</span></span>

3. <span data-ttu-id="8d511-130">使用 <xref:System.Configuration?displayProperty=nameWithType> 命名空間型別以：</span><span class="sxs-lookup"><span data-stu-id="8d511-130">Use the <xref:System.Configuration?displayProperty=nameWithType> namespace types to:</span></span>

    1. <span data-ttu-id="8d511-131">使用完整的類型名稱，將擴充功能新增至[ \<behaviorExtensions >](../../configure-apps/file-schema/wcf/behaviorextensions.md)區段，並鎖定元素。</span><span class="sxs-lookup"><span data-stu-id="8d511-131">Add the extension to the [\<behaviorExtensions>](../../configure-apps/file-schema/wcf/behaviorextensions.md) section using a fully-qualified type name and lock the element.</span></span>

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. <span data-ttu-id="8d511-132">將行為專案新增至`EndpointBehaviors` [ \<s >](../../configure-apps/file-schema/wcf/commonbehaviors.md)區段的屬性，並鎖定元素。</span><span class="sxs-lookup"><span data-stu-id="8d511-132">Add the behavior element to the `EndpointBehaviors` property of the [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) section and lock the element.</span></span> <span data-ttu-id="8d511-133">(若要在服務上安裝驗證器，驗證器必須是 <xref:System.ServiceModel.Description.IServiceBehavior> 並加入至 `ServiceBehaviors` 屬性)。下列程式碼範例將示範如何在步驟 a.</span><span class="sxs-lookup"><span data-stu-id="8d511-133">(To install the validator on the service, the validator must be an <xref:System.ServiceModel.Description.IServiceBehavior> and added to the `ServiceBehaviors` property.) The following code example shows the proper configuration after steps a.</span></span> <span data-ttu-id="8d511-134">和 b. 後進行適當的設定，唯一的例外是沒有強式名稱時。</span><span class="sxs-lookup"><span data-stu-id="8d511-134">and b., with the sole exception that there is no strong name.</span></span>

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. <span data-ttu-id="8d511-135">儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="8d511-135">Save the machine.config file.</span></span> <span data-ttu-id="8d511-136">下列程式碼範例執行步驟 3 中所有的工作，但將修改過的 machine.config 檔案複本儲存在本機上。</span><span class="sxs-lookup"><span data-stu-id="8d511-136">The following code example performs all the tasks in step 3 but saves a copy of the modified machine.config file locally.</span></span>

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a><span data-ttu-id="8d511-137">範例</span><span class="sxs-lookup"><span data-stu-id="8d511-137">Example</span></span>

<span data-ttu-id="8d511-138">下列程式碼範例示範如何將通用行為新增至 machine.config 檔案，並將複本儲存至磁碟上。</span><span class="sxs-lookup"><span data-stu-id="8d511-138">The following code example shows how to add a common behavior to the machine.config file and save a copy to the disk.</span></span> <span data-ttu-id="8d511-139">`InternetClientValidatorBehavior` 取自[安全性驗證](../samples/security-validation.md)範例。</span><span class="sxs-lookup"><span data-stu-id="8d511-139">The `InternetClientValidatorBehavior` is taken from the [Security Validation](../samples/security-validation.md) sample.</span></span>

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a><span data-ttu-id="8d511-140">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="8d511-140">.NET Framework Security</span></span>

<span data-ttu-id="8d511-141">您可能也要加密組態檔項目。</span><span class="sxs-lookup"><span data-stu-id="8d511-141">You may also want to encrypt the configuration file elements.</span></span> <span data-ttu-id="8d511-142">如需詳細資訊，請參閱「請參閱」一節。</span><span class="sxs-lookup"><span data-stu-id="8d511-142">For more information, see the See Also section.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d511-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d511-143">See also</span></span>

- [<span data-ttu-id="8d511-144">使用 DPAPI 加密設定檔元素</span><span class="sxs-lookup"><span data-stu-id="8d511-144">Encrypting configuration file elements using DPAPI</span></span>](https://go.microsoft.com/fwlink/?LinkId=94954)
- [<span data-ttu-id="8d511-145">使用 RSA 加密設定檔元素</span><span class="sxs-lookup"><span data-stu-id="8d511-145">Encrypting configuration file elements using RSA</span></span>](https://go.microsoft.com/fwlink/?LinkId=94955)
