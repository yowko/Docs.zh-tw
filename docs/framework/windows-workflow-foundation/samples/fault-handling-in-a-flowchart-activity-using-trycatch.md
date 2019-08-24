---
title: 使用 TryCatch 錯誤處理流程圖活動
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 42eb660aff01c7e29227c28a6ad0d47d4370eb91
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016023"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>使用 TryCatch 錯誤處理流程圖活動

這個範例示範 <xref:System.Activities.Statements.TryCatch> 活動在複雜控制流程活動中的使用方式。

在這個範例中，促銷碼和小孩人數會當做變數傳遞至 <xref:System.Activities.Statements.Flowchart> 活動，根據對應於促銷碼的公式來計算折扣。 此範例包含命令式程式碼和工作流程設計工具的範例版本。

下表詳細說明 `CreateFlowchartWithFaults` 活動的變數。

|參數|說明|
|----------------|-----------------|
|promoCode|促銷碼。 類型：String<br /><br /> 可能的值，說明放在括號中：<br /><br /> -單一 (單一)<br />-MNK (結婚, 沒有小孩)。<br />-MWK (與兒童結婚)。|
|numKids|小孩人數。 類型：int|

`CreateFlowchartWithFaults` 活動使用 <xref:System.Activities.Statements.FlowSwitch%601> 活動，在 `promoCode` 引數上切換，並透過下列公式計算折扣。

|`promoCode` 的值|折扣 (%)|
|--------------------------|--------------------|
|Single|10|
|MNK|15|
|MWK|15 + (1 – 1/`numberOfKids`)\*10**注意:** 此計算可能會擲回 <xref:System.DivideByZeroException>。 因此，折扣計算是包裝在 <xref:System.Activities.Statements.TryCatch> 活動中，以攔截 <xref:System.DivideByZeroException> 例外狀況並將折扣設為零。|

#### <a name="to-use-this-sample"></a>若要使用這個範例

1. 使用 Visual Studio 2010, 開啟 [FlowchartWithFaultHandling] 方案檔。

2. 若要建置此方案，請按 CTRL+SHIFT+B。

3. 若要執行此方案，請按 F5。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a>另請參閱

- [流程圖工作流程](../flowchart-workflows.md)
- [例外狀況](../exceptions.md)
