---
title: "下載驗證簽發者名稱登錄套件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d7aa4e4010da70f90bb18db9cd4e8179925bb58d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a>下載驗證簽發者名稱登錄套件
本主題討論如何在您的專案中下載與使用驗證簽發者名稱登錄 (VINR)。  
  
## <a name="downloading-the-validating-issuer-name-registry"></a>下載驗證簽發者名稱登錄  
 VINR 以 NuGet 套件的形式供您使用，會將必要的組件和參考新增至您的專案。 如果尚未安裝 NuGet，請移至 [nuget.org](http://nuget.org) 安裝它。 您可以在 NuGet 前往其頁面，查看延伸模組的版本控制記錄：[Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/) (NuGet 上的 Microsoft 驗證簽發者名稱登錄)。  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a>使用套件管理員 GUI 下載驗證簽發者名稱登錄  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下方案總管中的專案，然後選取 [管理 NuGet 套件]。  
  
2.  在 [管理 NuGet 套件] 視窗中，按一下搜尋方塊並輸入 `ValidatingIssuerNameRegistry`，然後按 **Enter**。  
  
3.  從 [結果] 窗格中，按一下第一個結果的 [安裝] 按鈕。  
  
4.  即開始下載套件。 在它新增至您的專案之前，[接受授權] 對話方塊會先出現。 如果您同意授權條款，請按一下 [接受]。  
  
5.  最新的 VINR 組件會下載並新增至您的專案。  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a>使用套件管理器主控台下載驗證簽發者名稱登錄  
  
1.  在 Visual Studio 中，依序按一下 [工具]、[程式庫套件管理員] 和 [套件管理器主控台]。  
  
2.  [套件管理器主控台] 視窗隨即開啟。 輸入下列文字，然後按 **ENTER**：  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  最新的 VINR 組件會下載並新增至您的專案。
