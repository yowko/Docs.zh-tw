---
title: "下載 JSON Web 語彙基元處理常式套件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: 3
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 3
---
# 下載 JSON Web 語彙基元處理常式套件
這個主題討論如何在專案中下載和使用 JSON Web 權杖處理常式。  
  
## 下載 JSON Web 語彙基元處理常式  
 JSON Web 權杖處理常式擴充已提供做為 NuGet 封裝，可將必要的組件和參考加入至您的專案。  如果您還未安裝 NuGet，請移至 [nuget.org](http://nuget.org) \(英文\) 進行安裝。  您可以瀏覽 NuGet 上的頁面，看到擴充功能的版本歷程記錄：[NuGet 上的 JSON Web 權杖處理常式](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)  
  
#### 使用封裝管理員 GUI 下載 JSON Web 語彙基元處理常式  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下 \[**方案總管**\] 中的專案，然後選取 \[**Manage NuGet Packages**\]。  
  
2.  在 \[**管理 NuGet 封裝**\] 視窗中，按一下搜尋方塊並輸入 `JWT Token Handler`，再按 **Enter** 鍵。  
  
3.  從結果窗格中，按一下第一個結果的 \[安裝\] 按鈕。  
  
4.  封裝會開始下載。  在將其加入至您的專案之前，會出現接受授權對話方塊。  如果您同意授權條款，請按一下 \[**我接受**\]。  
  
5.  最新的 JSON Web 權杖處理常式組件將會下載並加入至您的專案。  
  
#### 使用封裝管理員主控台下載 JSON Web 語彙基元處理常式  
  
1.  在 Visual Studio 中，按一下 \[**工具**\]、\[**程式庫封裝管理員**\] 和 \[**封裝管理員主控台**\]。  
  
2.  \[**封裝管理員主控台** \] 視窗隨即出現。  輸入下列文字，並按 **Enter** 鍵：  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  最新的 JSON Web 權杖處理常式組件將會下載並加入至您的專案。