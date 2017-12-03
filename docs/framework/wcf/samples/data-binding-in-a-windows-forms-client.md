---
title: "Windows Forms 用戶端中的資料繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 905d010c1ecdab1fc7b2c99e6d720b85ad40be32
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="data-binding-in-a-windows-forms-client"></a>Windows Forms 用戶端中的資料繫結
這個範例會示範如何在 Windows Form 應用程式中繫結 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務所傳回的資料。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本文的結尾。  
  
 這個範例會示範實作可定義要求-回覆通訊模式之合約的服務。 此範例是由用戶端 Windows Forms 應用程式 (.exe)，以及網際網路資訊服務 (IIS) 裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務所組成。  
  
 合約是由 `IWeatherService` 介面所定義，而該介面會公開 (Expose) 名為 `GetWeatherData` 的作業。 這項作業會接受城市陣列並傳回 `WeatherData` 物件的陣列，而這些物件表示某個城市的最高和最低預測溫度。  
  
 資料繫結 (Data Binding) 會發生在 Windows Forms 應用程式的用戶端上。 `DataGridView` 為資料的圖形表示，定義於 Windows Forms 設計工具中。 此外，還會建立名為 `BindingSource` 的媒介。 而 `BindingSource` 的資料來源會設為服務所傳回的資料陣列。 `BindingSource` 的目的在於提供資料和資料檢視之間的間接取值 (Indirection) 層。 所有的資料互動 (例如巡覽、排序、篩選和更新) 都會透過呼叫 `BindingSource` 元件來完成。 為了要完成 `DataGridView` 的資料繫結，`datasource` 的 `DataGridView` 會接著設為 `BindingSource` 物件。 然後，從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務傳回的所有資料會以圖形方式顯示給使用者。  每次使用者按一下按鈕，傳回的資料就會在資料繫結的 `DataGridView` 中自動更新。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a>另請參閱
