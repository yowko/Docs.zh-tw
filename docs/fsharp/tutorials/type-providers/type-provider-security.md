---
title: 型別提供者安全性
description: 深入了解中的型別提供者安全性F#，包括如何變更型別提供者的信任設定。
ms.date: 05/16/2016
ms.openlocfilehash: 9ccb33d7298736c3d6b54980b6fe09bc9f2e0259
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611187"
---
# <a name="type-provider-security"></a>型別提供者安全性

型別提供者是所參考組件 (Dll) 您F#專案或指令碼包含連接至外部資料來源，並呈現此型別資訊的程式碼F#類型的環境。 一般而言，參考組件中的程式碼才會執行當您編譯和接著執行程式碼 (或在指令碼的情況下傳送的程式碼F#互動式)。 不過，型別提供者組件會執行在 Visual Studio 中，當程式碼只是已在編輯器中瀏覽。 這是因為型別提供者需要執行額外的資訊，加入編輯器，例如 快速諮詢工具提示，IntelliSense 完成等等。 如此一來，有一些額外的安全性考量的型別提供者組件，因為它們會自動在 Visual Studio 處理序內執行。

## <a name="security-warning-dialog"></a>安全性警告對話方塊

當第一次使用特定的型別提供者組件，Visual Studio 會顯示警告型別提供者是執行 [安全性] 對話方塊。 Visual Studio 會載入型別提供者之前，它可讓您決定您是否信任此特定的提供者的機會。 如果您信任來源的型別提供者，然後選取 「 我信任此型別提供者 」。 如果您不信任來源的型別提供者，然後選取 我不信任此型別提供者。 」 信任的提供者，讓它能夠在 Visual Studio 內執行，並提供 IntelliSense 及建置功能。 但是，如果惡意型別提供者本身，執行其程式碼可能會危害您的電腦。

如果您的專案會包含參考型別提供者，您選擇在對話方塊中不信任的程式碼，然後在編譯時期，編譯器會報告錯誤，指出型別提供者不受信任。 相依於不受信任的型別提供者的任何型別會以紅色波浪線表示。 它可以安全地瀏覽程式碼編輯器中。

如果您決定要變更直接在 Visual Studio 中的信任設定，請執行下列步驟。

### <a name="to-change-the-trust-settings-for-type-providers"></a>若要變更型別提供者信任設定

1. 在上`Tools`功能表上，選取`Options`，然後展開`F# Tools`節點。

2. 選取`Type Providers`，在型別提供者清單中，型別提供者信任時，請選取此核取方塊並清除那些您不信任的核取方塊。

## <a name="see-also"></a>另請參閱

- [類型提供者](index.md)