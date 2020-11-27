---
title: 尋找清單項目的 UI 自動化項目
description: 若要瞭解如何在已知專案的索引時尋找清單專案的消費者介面自動化專案，請參閱範例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 95f6b558cc53b00701232f247f8de7f8c603e3ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276473"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>尋找清單項目的 UI 自動化項目

> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主題說明如何在 <xref:System.Windows.Automation.AutomationElement> 已知專案的索引時，針對清單中的專案取得。  
  
## <a name="example"></a>範例  

 下列範例示範兩種從清單中取出指定專案的方式，一個使用， <xref:System.Windows.Automation.TreeWalker> 另一個使用 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 。  
  
 第一個技巧對 Win32 控制項來說可能比較快，但第二個技巧更快 Windows Presentation Foundation (WPF) 控制項。  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>另請參閱

- [取得 UI 自動化項目](obtaining-ui-automation-elements.md)
