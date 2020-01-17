---
title: 將 .NET 遠端處理應用程式移轉到 WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 1d7edab8ad89660f3384d0ccf556384175c4d5db
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212155"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>將 .NET 遠端處理應用程式移轉到 WCF
**本主題專屬於為了與現有應用程式提供回溯相容性而保留的舊版技術，不建議用於新的開發。分散式應用程式現在應該使用 WCF 進行開發。**  
  
 有兩種方式可利用 WCF 與現有 .NET 遠端處理應用程式：整合與遷移。 整合可讓您讓 .NET 遠端處理2.0 和 WCF 並存執行，讓您同時公開兩種技術的相同商務物件，而不需要修改現有的 .NET 遠端2.0 程式碼。 整合需要您在 .NET Framework 2.0 或更新版本上執行。 如果您想要利用 WCF 功能，而不需要與遠端2.0 系統的連線相容性，您可以將整個服務遷移至 WCF。 從 .NET 遠端處理2.0 遷移至 WCF 需要對遠端物件的介面和其設定進行變更。 [從遠端處理到 Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80))都涵蓋這兩個主題。  
  
## <a name="see-also"></a>請參閱

- [概念性概觀](../../../../docs/framework/wcf/conceptual-overview.md)
