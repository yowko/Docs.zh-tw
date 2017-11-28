---
title: "根據屬性條件尋找 UI 自動化項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cafd84ce3acea80905d686f33f23338e3581a9c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>根據屬性條件尋找 UI 自動化項目
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題包含範例程式碼，說明如何找出內的項目[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]樹狀結構會根據特定的屬性或屬性。  
  
## <a name="example"></a>範例  
 下列範例中，一組屬性的條件，找出感興趣的某些項目 （或項目） 中指定<xref:System.Windows.Automation.AutomationElement>樹狀目錄中。 搜尋所有相符項目則會執行與<xref:System.Windows.Automation.AutomationElement.FindAll%2A>方法，其中包含一系列的<xref:System.Windows.Automation.AndCondition>布林作業之相符項目數目。  
  
> [!NOTE]
>  從搜尋時<xref:System.Windows.Automation.AutomationElement.RootElement%2A>，您應該試著取得直接子系。 如果搜尋子系可能會逐一查看數百或甚至數千個項目，但可能會造成堆疊溢位。 如果您嘗試取得較低層級的特定項目，您就應該要從應用程式視窗或較低層級的容器開始搜尋。  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>另請參閱  
 [InvokePattern 和 ExpandCollapsePattern 功能表項目範例](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [取得 UI 自動化項目](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [使用 AutomationID 屬性](../../../docs/framework/ui-automation/use-the-automationid-property.md)
