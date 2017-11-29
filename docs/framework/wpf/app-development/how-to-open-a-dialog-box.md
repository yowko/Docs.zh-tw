---
title: "如何： 開啟的對話方塊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d318f35f8f009f0f2c77210ca8b6b29bedfb7619
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-open-a-dialog-box"></a>如何： 開啟的對話方塊
這個範例示範如何開啟的對話方塊。  
  
## <a name="example"></a>範例  
 對話方塊是開啟的視窗，藉由執行個體化<xref:System.Windows.Window>，然後呼叫<xref:System.Windows.Window.ShowDialog%2A>方法。 <xref:System.Windows.Window.ShowDialog%2A>會開啟視窗並不會在關閉新的對話方塊之前傳回。 這類視窗就是所謂*強制回應*視窗中，並限制使用者輸入。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 呼叫<xref:System.Windows.Window.ShowDialog%2A>需要使用所有視窗和不受限制的使用者輸入的事件的權限。  
  
## <a name="see-also"></a>另請參閱  
 [傳回對話方塊結果](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)
