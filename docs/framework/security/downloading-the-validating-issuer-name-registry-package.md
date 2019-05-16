---
title: 下載驗證簽發者名稱登錄套件
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 5684844f1db33b075df099b3026d9d0c1061199f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631852"
---
# <a name="download-the-validating-issuer-name-registry-package"></a>下載驗證簽發者名稱登錄套件

本主題討論如何在您的專案中下載與使用驗證簽發者名稱登錄 (VINR)。

VINR 以 NuGet 套件的形式供您使用，會將必要的組件和參考新增至您的專案。 如果尚未安裝 NuGet，請移至 [nuget.org](https://nuget.org) 安裝它。 在 NuGet 前往其頁面，您可以看到延伸模組的版本歷程記錄：[Microsoft 驗證簽發者名稱登錄在 NuGet 上](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)

## <a name="use-the-package-manager-gui"></a>使用套件管理員 GUI

1. 在 Visual Studio 中，以滑鼠右鍵按一下方案總管中的專案，然後選取 [管理 NuGet 套件]。

2. 在 [管理 NuGet 套件] 視窗中，按一下搜尋方塊並輸入 `ValidatingIssuerNameRegistry`，然後按 **Enter**。

3. 從 [結果] 窗格中，按一下第一個結果的 [安裝] 按鈕。

4. 即開始下載套件。 在它新增至您的專案之前，[接受授權] 對話方塊會先出現。 如果您同意授權條款，請按一下 [接受]。

5. 最新的 VINR 組件會下載並新增至您的專案。

## <a name="use-the-package-manager-console"></a>使用套件管理員主控台

1. 在 Visual Studio 中，按一下**工具** > **NuGet 套件管理員** > **Package Manager Console**。

2. [套件管理器主控台] 視窗隨即開啟。 輸入下列文字，然後按 **ENTER**：

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. 最新的 VINR 組件會下載並新增至您的專案。
