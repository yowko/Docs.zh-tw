---
title: 型別提供者安全性
description: '深入了解在 F # 中，包括如何變更型別提供者的信任設定的型別提供者安全性。'
ms.date: 05/16/2016
ms.openlocfilehash: 66a873a32029d706f1f6fab50dd4f93bc29bca03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="type-provider-security"></a>型別提供者安全性

型別提供者是包含組件 (Dll) 參考 F # 專案或指令碼的程式碼，以連接至外部資料來源和 F # 型別環境介面此類型資訊。 通常，當您編譯和接著執行程式碼 （或指令碼時，請將驗證碼傳送至 F # Interactive），是只執行參考組件中的程式碼。 不過，型別提供者組件會執行在 Visual Studio 中，只是在編輯器中瀏覽程式碼時。 這是因為型別提供者需要執行額外的資訊加入至編輯器，例如快速諮詢工具提示，IntelliSense 完成等等。 如此一來，有額外的安全性考量的型別提供者組件，因為它們會自動執行 Visual Studio 處理序內。


## <a name="security-warning-dialog"></a>安全性警告對話方塊
當第一次使用特定型別提供者組件，Visual Studio 會顯示 [安全性] 對話方塊會警告您的型別提供者即將執行。 Visual Studio 會載入型別提供者之前，它讓您決定是否信任這個特定的提供者。 如果您信任來源的型別提供者，然後選取 我信任此型別提供者 」。 如果您不信任來源的型別提供者，然後選取 我不信任此型別提供者。 」 信任的提供者，讓它能夠在 Visual Studio 內執行，並提供 IntelliSense 然後建置功能。 但是，如果惡意型別提供者本身，執行其程式碼可能會危及您的電腦。

如果您的專案包含參考型別提供者，您選擇在對話方塊中不信任的程式碼，然後在編譯時期，編譯器會回報錯誤，指出類型提供者未受信任。 任何相依於不受信任的類型提供者的類型會以紅色波浪線表示。 它可以安全地瀏覽程式碼編輯器中。

如果您決定要變更的信任設定，直接在 Visual Studio 中，執行下列步驟。


#### <a name="to-change-the-trust-settings-for-type-providers"></a>若要變更型別提供者信任設定

1. 在`Tools`功能表上，選取`Options`，然後展開`F# Tools`節點。
<br />

2. 選取`Type Providers`中的型別提供者清單中，選取核取方塊的型別提供者信任時，和不信任的清除核取方塊。
<br />


## <a name="see-also"></a>另請參閱
[類型提供者](index.md)
