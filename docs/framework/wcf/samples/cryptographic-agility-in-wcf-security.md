---
title: WCF 安全性中的密碼編譯靈活性
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714929"
---
# <a name="cryptographic-agility-in-wcf-security"></a>WCF 安全性中的密碼編譯靈活性

這個範例示範如何在標準/自訂演算法中指定，以在 Windows Communication Foundation （WCF）用戶端和服務中提供密碼編譯 agile 執行。 此範例是由下列專案所組成：

**Service**

這是自我裝載的 WCF 服務，可執行 `ICalculator` 介面，並使用已停用安全會話和可靠會話的 <xref:System.ServiceModel.WSHttpBinding> 來保護端點。 這項服務會定義自訂的 `SecurityAlgorithmSuite` 類別，以指定用於訊息安全性的密碼編譯演算法。

**用戶端**

這是在成功驗證之後，會存取服務的 WCF 用戶端。 它會叫用由 `ICalculator` 介面公開並且由服務實作的作業。 這個用戶端還會定義相同的自訂 `SecurityAlgorithmSuite` 類別，以指定用於訊息安全性的密碼編譯演算法。

## <a name="to-use-this-sample"></a>若要使用這個範例

1. 在 Visual Studio 2012 中開啟 [CryptoAgility] 方案。

2. 按下 CTRL+SHIFT+B 以建置方案。

3. 開啟 [檔案瀏覽器] 並流覽至 [\WCF\Basic\Security\CryptoAgility\Service\bin] 目錄，並以滑鼠右鍵按一下 [setup.exe]，然後選取 [以**系統管理員身分執行**]，以系統管理員許可權執行此服務 .exe 檔案。

4. 巡覽至 \WCF\Basic\Security\CryptoAgility\Client\bin 目錄，並正常執行 client.exe 檔。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>請參閱

- [Windows Communication Foundation 安全性](../feature-details/security.md)
