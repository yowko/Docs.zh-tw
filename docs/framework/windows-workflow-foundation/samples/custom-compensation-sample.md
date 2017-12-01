---
title: "自訂補償範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 088e8e771d5fea60987e7ac53ebad0d3fef24b5d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="custom-compensation-sample"></a>自訂補償範例
這個範例示範如何使用 <xref:System.Activities.Statements.CompensableActivity> 及其補償處理常式，定義自訂的補償邏輯。 這個範例中的模型案例為卡車租賃業者。  
  
## <a name="sample-details"></a>範例詳細資料  
 模擬的步驟如下：  
  
1.  使用者要求給定日期的卡車租賃報價。  
  
2.  連絡三家卡車公司，並提供三份報價。  
  
3.  使用者選取一份卡車報價，開始著手用信用卡訂購。  
  
4.  應用程式取消其他兩份卡車報價。  
  
5.  如果在預定日期前 10 天 (含) 內取消，應用程式針對非尊榮客戶收取不退費的服務費。  
  
6.  應用程式收取卡車租賃費用。  
  
7.  應用程式等候，直到預定日期或客戶決定取消預定為止，依先到日期為準。  
  
8.  如果客戶取消預定，<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 自訂補償邏輯會依據下列邏輯執行：  
  
    1.  如果客戶不是尊榮客戶，而且在預定日期前 10 天內，仍會收取服務費，否則應用程式會針對服務費全額退費。  
  
    2.  其餘可補償活動 (卡車租車 + 卡車租車費) 會依據預設補償邏輯執行，也就是反向執行的補償。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CustomCompensation.sln 方案。 此檔案位於 \WF\Basic\Compensation\CustomCompensation 目錄中。  
  
2.  按下 CTRL+SHIFT+B 以建置方案。  
  
3.  按 CTRL + F5 執行應用程式。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`