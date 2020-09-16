---
title: 作法：鎖定企業的端點
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 68a7b80a01d9b1a8c5243331e63a1b82996e8ee6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558143"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>作法：鎖定企業的端點

大型企業通常需要在遵循企業安全性原則的環境中開發應用程式。 下列主題討論如何開發和安裝用戶端端點驗證程式，以用來驗證電腦上安裝的所有 Windows Communication Foundation (WCF) 用戶端應用程式。

在此情況下，驗證程式是用戶端驗證程式，因為此端點行為會加入至 machine.config 檔案中的用戶端 [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) 區段。 WCF 只會載入用戶端應用程式的一般端點行為，並且只會為服務應用程式載入泛型服務行為。 若要為服務應用程式安裝這個相同的驗證器，驗證器必須是服務行為。 如需詳細資訊，請參閱 [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) 一節。

> [!IMPORTANT]
> <xref:System.Security.AllowPartiallyTrustedCallersAttribute>當應用程式在部分信任環境中執行時，不會執行未以屬性標示 (APTCA) 的服務或端點行為，因為當 [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) 應用程式在部分信任環境中執行時，並不會在發生這種情況時擲回例外狀況。 若要強制執行通用行為 (例如驗證器)，您必須執行下列其中一項：
>
> - 使用屬性標記您的通用行為 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ，讓它可以在部署為部分信任應用程式時執行。 請注意，您可以在電腦上設定登錄項目，以防止已標記 APTCA 的組件執行。
>
> - 確定應用程式是否部署為完全信任的應用程式，讓使用者無法修改程式碼存取安全性設定，以在部分信任環境中執行應用程式。 如果可以執行這項操作，自訂驗證器就不會執行，也不會擲回例外狀況。 若要確認這一點，請參閱 `levelfinal` 使用代碼啟用 [安全性原則工具 ( # A0) ](../../tools/caspol-exe-code-access-security-policy-tool.md)的選項。
>
> 如需詳細資訊，請參閱 [部分信任最佳做法](../feature-details/partial-trust-best-practices.md) 和 [支援的部署案例](../feature-details/supported-deployment-scenarios.md)。

### <a name="to-create-the-endpoint-validator"></a>若要建立端點驗證器

1. 以 <xref:System.ServiceModel.Description.IEndpointBehavior> 方法中所需的驗證步驟建立 <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A>。 範例請見下列程式碼。  (`InternetClientValidatorBehavior` 取自 [安全性驗證](../samples/security-validation.md) 範例。 ) 

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. 建立新的 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>，它會註冊步驟 1 中建立的端點驗證器。 下列程式碼範例會顯示這點。  (此範例的原始程式碼位於 [安全性驗證](../samples/security-validation.md) 範例中。 ) 

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. 請務必以強式名稱簽署編譯的組件。 如需詳細資訊，請參閱 [強式名稱工具 ( # A0) ](../../tools/sn-exe-strong-name-tool.md) 和您語言的編譯器命令。

### <a name="to-install-the-validator-into-the-target-computer"></a>若要將驗證器安裝至目標電腦

1. 使用適當的機制安裝端點驗證器。 在企業中，您可以使用群組原則和 Systems Management Server (SMS) 安裝端點驗證器。

2. 使用 [Gacutil.exe (全域組件快取工具) ](../../tools/gacutil-exe-gac-tool.md)，將強式名稱的元件安裝到全域組件快取中。

3. 使用 <xref:System.Configuration?displayProperty=nameWithType> 命名空間型別以：

    1. 使用完整型別名稱將延伸加入至 [\<behaviorExtensions>](../../configure-apps/file-schema/wcf/behaviorextensions.md) 區段，並鎖定元素。

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. 將行為專案加入至 `EndpointBehaviors` 區段的屬性 [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) ，並鎖定專案。  (在服務上安裝驗證程式時，驗證程式必須是 <xref:System.ServiceModel.Description.IServiceBehavior> ，並將其加入至 `ServiceBehaviors` 屬性。 ) 下列程式碼範例會顯示步驟 a 之後的適當設定。 和 b. 後進行適當的設定，唯一的例外是沒有強式名稱時。

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. 儲存 machine.config 檔。 下列程式碼範例執行步驟 3 中所有的工作，但將修改過的 machine.config 檔案複本儲存在本機上。

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a>範例

下列程式碼範例示範如何將通用行為新增至 machine.config 檔案，並將複本儲存至磁碟上。 `InternetClientValidatorBehavior`是取自[安全性驗證](../samples/security-validation.md)範例。

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a>.NET Framework 安全性

您可能也要加密組態檔項目。 如需詳細資訊，請參閱「請參閱」一節。

## <a name="see-also"></a>另請參閱

- [使用 DPAPI 的加密組態檔項目](/previous-versions/msp-n-p/ff647398(v=pandp.10))
- [使用 RSA 的加密組態檔項目](/previous-versions/msp-n-p/ff650304(v=pandp.10))
