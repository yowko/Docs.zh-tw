---
title: "AutoSize 在 TableLayoutPanel 控制項中的行為 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "自動調整大小"
  - "AutoSize 屬性, TableLayoutPanel 控制項"
  - "AutoSizeMode 屬性"
  - "控制項 [Windows Form], 調整大小"
  - "版面配置 [Windows Form], AutoSize"
  - "當地語系化表單"
  - "調整大小, 自動"
  - "TableLayoutPanel 控制項 [Windows Form], AutoSize 行為"
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# AutoSize 在 TableLayoutPanel 控制項中的行為
## 特定的 AutoSize 行為  
 <xref:System.Windows.Forms.TableLayoutPanel> 控制項支援下列方法的自動調整大小行為：  
  
-   透過 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性；  
  
-   透過在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的資料行和資料列樣式上的 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 屬性。  
  
### AutoSize 屬性與資料列和資料行樣式  
 下列資料表說明 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性與 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的資料行和資料列樣式之間的互動。  
  
|AutoSize 設定|樣式互動|  
|-----------------|----------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel> 控制項是從左至右進行處理，且為資料行或資料列或依下列順序配置空間。<br /><br /> 1.  如果 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 屬性是設定為 <xref:System.Windows.Forms.SizeType>，便會配置由 <xref:System.Windows.Forms.ColumnStyle.Width%2A> 或 <xref:System.Windows.Forms.RowStyle.Height%2A> 所指定的像素數目。<br />2.  如果 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 屬性是設定為 <xref:System.Windows.Forms.SizeType>，便會配置由子控制項的 <xref:System.Windows.Forms.Control.GetPreferredSize%2A> 方法所傳回的像素數目。<br />3.  在配置完所有 <xref:System.Windows.Forms.SizeType> 和 <xref:System.Windows.Forms.SizeType> 資料行或資料列的空間後，<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 設定為 <xref:System.Windows.Forms.SizeType> 的資料行或資料列，就會用來按比例配置剩餘的可用空間。|  
|`true`|類似於前一個互動，例外狀況是 <xref:System.Windows.Forms.SizeType> 資料行或資料列需要自動調整大小外觀。<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel> 控制項會展開資料行或資料列以建立足夠的可用空間，如此具有 <xref:System.Windows.Forms.SizeType> 樣式的資料行或資料列才不會裁剪它的內容。  <xref:System.Windows.Forms.TableLayoutPanel> 控制項會根據 <xref:System.Windows.Forms.ColumnStyle.Width%2A> 或 <xref:System.Windows.Forms.RowStyle.Height%2A> 屬性按比例配置新的空間。|  
  
## 請參閱  
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [TableLayoutPanel 控制項概觀](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)