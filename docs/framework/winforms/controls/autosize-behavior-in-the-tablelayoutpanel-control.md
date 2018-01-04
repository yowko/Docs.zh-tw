---
title: "AutoSize 在 TableLayoutPanel 控制項中的行為"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06bd0686b31b52ccb8580a545910339d2e2cd5bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>AutoSize 在 TableLayoutPanel 控制項中的行為
## <a name="distinct-autosize-behaviors"></a>相異 AutoSize 行為  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項支援自動調整大小行為如下：  
  
-   透過<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。  
  
-   透過<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性<xref:System.Windows.Forms.TableLayoutPanel>控制項的資料行和資料列樣式。  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>AutoSize 屬性與資料列和資料行樣式  
 下表描述之間的互動<xref:System.Windows.Forms.Control.AutoSize%2A>屬性和<xref:System.Windows.Forms.TableLayoutPanel>控制項的資料行和資料列樣式。  
  
|自動調整設定|樣式互動|  
|----------------------|-----------------------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel>控制會繼續從左到右，與資料行或資料列，或依下列順序配置空間。<br /><br /> 1.如果<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性設定為<xref:System.Windows.Forms.SizeType.Absolute>，所指定的像素數<xref:System.Windows.Forms.ColumnStyle.Width%2A>或<xref:System.Windows.Forms.RowStyle.Height%2A>配置。<br />2.如果<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性設定為<xref:System.Windows.Forms.SizeType.AutoSize>，傳回的子控制項的像素數<xref:System.Windows.Forms.Control.GetPreferredSize%2A>配置方法。<br />3.之後的所有空間<xref:System.Windows.Forms.SizeType.Absolute>和<xref:System.Windows.Forms.SizeType.AutoSize>資料行或資料列配置時，任何資料行或資料列<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>設<xref:System.Windows.Forms.SizeType.Percent>會用來按比例配置剩餘的可用空間|  
|`true`|類似於先前的互動，發生例外狀況，<xref:System.Windows.Forms.SizeType.Percent>資料行或資料列取得自動調整大小的長寬。<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>控制展開的資料行或資料列，以建立足夠的可用空間，讓任何資料行或資料列與<xref:System.Windows.Forms.SizeType.Percent>樣式裁剪其內容。 <xref:System.Windows.Forms.TableLayoutPanel>控制項配置的新空間等比例地根據<xref:System.Windows.Forms.ColumnStyle.Width%2A>或<xref:System.Windows.Forms.RowStyle.Height%2A>屬性。|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [TableLayoutPanel 控制項概觀](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
