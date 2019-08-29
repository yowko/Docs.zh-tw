---
title: 原生互通性 - .NET
description: 了解如何連接到 .NET 中的原生元件。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 3ca213bc7228d2e4337607df2d47b334c5bea14f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106810"
---
# <a name="native-interoperability"></a>原生互通性

下列文章說明在 .NET 中執行「原生互通性」的各種方式。

以下為您應呼叫機器碼的幾個原因︰

- 作業系統隨附大量受控類別庫中所沒有的 API。 此情節的基本範例將會說明存取硬體或作業系統管理功能。
- 與其他擁有或可產生 C 樣式 ABI (原生 ABI) 的元件通訊，像是透過 [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) 公開的 Java 程式碼，或是任何可產生原生元件的受控語言。
- 在 Windows 上，大部分的已安裝軟體 (例如 Microsoft Office 套件) 會註冊 COM 元件，這些元件代表其程式，且可讓開發人員予以自動化或使用。 而這也需要原生互通性。

上述清單並未涵蓋所有開發人員會想要，或必須與原生元件互動的可能情況和情節。 舉例來說，.NET 類別庫會使用原生互通性支援來實作其一部分的 API，例如主控台支援和操作、檔案系統存取權及其他項目。 不過請務必注意，您可視需要選擇使用。

> [!NOTE]
> 本節中大部分範例會針對 .NET Core 的所有三種支援平台 (Windows、Linux 和 macOS) 來呈現。 不過，對於一些簡短和說明性的範例，只會顯示一個使用 Windows 檔名和副檔名 (也就是代表程式庫的 "dll") 的範例。 這不表示您無法在 Linux 或 macOS 上使用這些功能，如此呈現只是為了方便起見。

## <a name="see-also"></a>另請參閱

- [平台叫用 (P/Invoke)](pinvoke.md)
- [型別封送處理](type-marshaling.md)
- [原生互通性最佳做法](best-practices.md)
