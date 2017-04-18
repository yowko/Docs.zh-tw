---
title: "TableLayoutPanel 控制項的最佳作法 | Microsoft Docs"
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
  - "最佳作法, TableLayoutPanel 控制項"
  - "控制項 [Windows Form], 調整大小"
  - "表單, 最佳作法"
  - "版面配置 [Windows Form]"
  - "版面配置 [Windows Form], 最佳作法"
  - "版面配置 [Windows Form], AutoSize"
  - "調整大小, 自動"
  - "TableLayoutPanel 控制項 [Windows Form], 最佳作法"
  - "TableLayoutPanel 控制項 [Windows Form], AutoSize 行為"
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# TableLayoutPanel 控制項的最佳作法
<xref:System.Windows.Forms.TableLayoutPanel> 控制項提供了強大的配置功能，您在 Windows Form 上使用這些功能之前應該先仔細考量。  
  
## 建議事項  
 下列建議將有助您充分利用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的優點。  
  
### 目標使用  
 盡量不要使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。  在所有需要調整配置大小的情況中都不應該使用此控制項。  下列清單描述從使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項獲益最多的配置：  
  
-   表單的多個部分會按彼此之間比例調整大小的配置。  
  
-   在執行階段時會動態修改或產生的配置，例如依照喜好設定加入或減去使用者可自訂欄位的資料輸入表單。  
  
-   應該維持在整體固定大小的配置。  例如，您可能有應該維持在小於 800 x 600 的對話方塊，但是需要支援當地語系化字串。  
  
 下列清單說明無法從使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項大幅獲益的配置：  
  
-   具有單一標籤資料行和單一文字輸入區資料行的簡單資料輸入表單。  
  
-   具有單一大型顯示區，應該在調整大小發生時填滿所有可用空間的表單。  其中一個範例是顯示單一 <xref:System.Windows.Forms.PropertyGrid> 控制項的表單。  在這種情況下請使用錨定 \(Anchor\)，因為在調整表單大小時不應該展開其他內容。  
  
 請小心選擇需要在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中的控制項。  如果您有空間可以使用錨定讓文字變大 30% ，請考慮只使用 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性。  如果您可以估計配置所需要的空間，使用 <xref:System.Windows.Forms.Control.Dock%2A> 和 <xref:System.Windows.Forms.Control.Anchor%2A> 會比評估剩餘空間和 <xref:System.Windows.Forms.Control.AutoSize%2A> 行為的詳細資料更為容易。  
  
 一般來說，當使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項設計配置時，請盡量保持設計的簡單化。  
  
### 使用文件大綱視窗  
 \[文件大綱\] 視窗提供配置的樹狀結構檢視，您可以用來管理控制項的疊置順序 \(Z\-order\) 和父\-子關係 \(Parent\-Child Relationship\)。  請從 \[**檢視**\] 功能表中，選取 \[**其他視窗**\]，然後選取 \[**文件大綱**\]。  
  
### 避免巢狀結構  
 避免 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中有其他 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的巢狀結構。  巢狀配置的偵錯可能會很困難。  
  
### 避免視覺化繼承  
 <xref:System.Windows.Forms.TableLayoutPanel> 控制項不支援在 Windows Forms 設計工具中的視覺化繼承。  在設計階段，衍生類別的 <xref:System.Windows.Forms.TableLayoutPanel> 控制項將顯示為「已鎖定」。  
  
## 請參閱  
 <xref:System.Windows.Forms.TableLayoutPanel>   
 <xref:System.Windows.Forms.FlowLayoutPanel>