---
title: 將 .NET 遠端處理應用程式移轉到 WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 4040fb0ac223f91705a49b733f6a1f42d144068e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046602"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>將 .NET 遠端處理應用程式移轉到 WCF
**本主題專門說明一項為了在現有應用程式中提供回溯相容性而保留的舊有技術，不建議用於新的開發工作。分散式應用程式現在應該使用 WCF 進行開發。**  
  
 有兩種方式可利用 WCF 與現有的.NET 遠端處理應用程式： 整合與移轉。 整合可讓您可使用.NET Remoting 2.0 和 WCF 並存執行，讓您不需要修改現有的.NET Remoting 2.0 程式碼同時公開相同的商務物件兩種技術。 整合需要在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 (含) 以上版本執行。 如果您想要利用 WCF 功能，而不需要與 Remoting 2.0 系統的網路相容性，您可以將整個服務移轉至 WCF。 從.NET Remoting 2.0 移轉至 WCF 需要變更遠端物件的介面和其組態設定。 這些主題所述[從遠端處理到 Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403)。  
  
## <a name="see-also"></a>另請參閱

- [概念性概觀](../../../../docs/framework/wcf/conceptual-overview.md)
