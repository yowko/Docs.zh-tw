---
title: 本機通道
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 87e140395ac2fb5702d8655cf970da8a60c991ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144503"
---
# <a name="local-channel"></a>本機通道
本地通道是用於同一應用程式域內通信的 Windows 通信基礎 （WCF） 傳輸通道。 這個通道在用戶端和服務於相同應用程式定義域中執行，而必須避免一般 WCF 通道堆疊的負荷 (序列化和還原序列化訊息) 時相當實用。  
  
## <a name="demonstrates"></a>示範  
 本機通道  
  
## <a name="discussion"></a>討論區  
 此範例包含二個專案檔：  
  
- **本地通道**：當前應用程式域中本地通道的程式設計表示形式。 在此專案中，傳送的元件會將訊息放入記憶體內部佇列，而接收元件則會取消訊息佇列並接收該訊息。  
  
- **用戶端和服務**：此專案在主控台應用程式中託管服務，然後運行用戶端以從同一應用程式域中調用該服務。  
  
 本機通道的設計在於同時略過通道堆疊和序列化程序，以加快速度。 本機傳輸通道是使用佇列實作，以便將服務呼叫從用戶端傳輸至服務，以及將值傳回到用戶端。 這個範例不會序列化參數和傳回值，而會複製物件。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 建置及執行 LocalChannel 方案。  
  
2. 服務主機會啟動，而用戶端會使用本機通道呼叫服務。 主控台視窗隨即出現，並顯示服務呼叫的結果。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
