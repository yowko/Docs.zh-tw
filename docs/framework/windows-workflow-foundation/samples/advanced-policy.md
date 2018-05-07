---
title: 進階原則
ms.date: 03/30/2017
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
ms.openlocfilehash: 81cf2fb428833d4ca8cccf197011b69f2ccf3108
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="advanced-policy"></a>進階原則
這個範例會延續簡單原則範例。 除了簡單原則範例的住家折扣和商務折扣規則外，還新增數個規則。  
  
 新增了高額規則，為高額訂單提供更大的折扣。 此規則的優先順序值小於前兩個規則，因此它會覆寫折扣欄位，並且優先順序高於住家及商務折扣規則。  
  
 此外，還新增了計算總額規則，此規則會根據折扣等級計算總額， 並說明如何參考工作流程活動定義的方法，以及如何使用其他動作。 這個規則還會示範鏈結行為，因為每當折扣欄位變更時，就會評估一次。 此外，CalculateTotal 方法的方法屬性設定顯示為 RuleWriteAttribute。 這使得每次執行方法時，都會重新評估受影響的規則 (ErrorTotalRule)。  
  
 最後新增的規則是偵測錯誤的規則 (在此例中，Total 小於 0)。 如果偵測到錯誤，就會暫止執行原則。  
  
 最後，將 `Console.Writeline` 呼叫當做動作新增至每個規則，以提高規則執行的可視性，而且這也表示可以存取參照類型上的靜態方法。 您也可以使用追蹤來取得所執行規則的可視性。  
  
 這個範例使用的規則包括：  
  
 **ResidentialDiscountRule:**  
  
 IF OrderValue > 500 AND CustomerType = Residential  
  
 THEN Discount = 5%  
  
 **BusinessDiscountRule:**  
  
 IF OrderValue > 10000 AND CustomerType = Business  
  
 THEN Discount = 10%  
  
 **HighValueDiscountRule:**  
  
 IF OrderValue > 20000  
  
 THEN Discount = 15%  
  
 **TotalRule:**  
  
 IF Discount > 0  
  
 THEN CalculateTotal(OrderValue, Discount)  
  
 ELSE Total = OrderValue  
  
 **ErrorTotalRule:**  
  
 如果總\<0  
  
 THEN Error = "Fired ErrorTotalRule"; Halt  
  
 透過追蹤，您還可以觀察到規則的評估和執行。  
  
### <a name="to-build-the-sample"></a>若要建置範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。  
  
2.  按 CTRL+SHIFT+B 建置此方案。  
  
3.  按 CTRL+F5 執行方案，但不進行偵錯。  
  
### <a name="to-run-the-sample"></a>若要執行範例  
  
-   在 [SDK 命令提示字元] 視窗中，執行 AdvancedPolicy\bin\debug 資料夾 (若是範例的 Visual Basic 版本，則是 AdvancedPolicy \bin 資料夾) 中的 .exe 檔案，該資料夾位於此範例的主要資料夾下方。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [簡單原則](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
