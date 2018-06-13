---
title: 下載 JSON Web 語彙基元處理常式套件
ms.date: 03/30/2017
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 5a4846a5ec92324105f41b320d0d77f8749c28f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404673"
---
# <a name="downloading-the-json-web-token-handler-package"></a>下載 JSON Web 語彙基元處理常式套件
本主題討論如何在您的專案中下載並使用 JSON Web 權杖處理常式。  
  
## <a name="downloading-the-json-web-token-handler"></a>下載 JSON Web 語彙基元處理常式  
 JSON Web 權杖處理常式延伸模組以 NuGet 套件的形式供您使用，會將必要的組件和參考新增至您的專案。 如果尚未安裝 NuGet，請移至 [nuget.org](http://nuget.org) 安裝它。 您可以在 NuGet 前往其頁面，查看延伸模組的版本控制記錄：[JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/) (NuGet 上的 JSON Web 權杖處理常式)。  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a>使用套件管理員 GUI 下載 JSON Web 權杖處理常式  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下方案總管中的專案，然後選取 [管理 NuGet 套件]。  
  
2.  在 [管理 NuGet 套件] 視窗中，按一下搜尋方塊並輸入 `JWT Token Handler`，然後按 **Enter**。  
  
3.  從 [結果] 窗格中，按一下第一個結果的 [安裝] 按鈕。  
  
4.  即開始下載套件。 在它新增至您的專案之前，[接受授權] 對話方塊會先出現。 如果您同意授權條款，請按一下 [接受]。  
  
5.  最新的 JSON Web 權杖處理常式會下載並新增至您的專案。  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a>使用套件管理員主控台下載 JSON Web 權杖處理常式  
  
1.  在 Visual Studio 中，依序按一下 [工具]、[程式庫套件管理員] 和 [套件管理器主控台]。  
  
2.  [套件管理器主控台] 視窗隨即開啟。 輸入下列文字，然後按 **ENTER**：  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  最新的 JSON Web 權杖處理常式會下載並新增至您的專案。
