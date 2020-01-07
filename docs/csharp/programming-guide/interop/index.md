---
title: 互通性 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 64fac0245dcf5976786b51e0d96b795b8b1e5d68
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635193"
---
# <a name="interoperability-c-programming-guide"></a>互通性 (C# 程式設計手冊)
互通性可讓您保留並充分利用目前在 Unmanaged 程式碼上的投資。 在 Common Language Runtime (CLR) 控制下執行的程式碼稱為「Managed 程式碼」，而在 CLR 外部執行的程式碼稱為「Unmanaged 程式碼」。 COM、COM+、C++ 元件、ActiveX 元件及 Microsoft Windows API 都是 Unmanaged 程式碼的範例。  
  
 .NET Framework 會透過平台叫用服務、<xref:System.Runtime.InteropServices> 命名空間、C++ 互通性及 COM 互通性 (COM Interop)，啟用與非受控程式碼的互通性。  
  
## <a name="in-this-section"></a>本章節內容  
 [互通性概觀](./interoperability-overview.md)  
 說明要在 C# Managed 程式碼和 Unmanaged 程式碼之間相互操作的方法。  
  
 [如何使用C#功能存取 Office interop 物件](./how-to-access-office-onterop-objects.md)  
 說明在 Visual C# 中引進以利 Office 程式設計的功能。  
  
 [如何在 COM Interop 程式設計中使用已編制索引的屬性](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 說明如何使用已索引的屬性來存取具有參數的 COM 屬性。  
  
 [如何使用平台叫用來播放 WAV 檔案](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 說明如何在 Windows 作業系統上使用平台叫用服務來播放 .wav 音效檔。  
  
 [逐步解說：Office 程式設計](./walkthrough-office-programming.md)  
 示範如何建立 Excel 活頁簿以及包含對該活頁簿之連結的 Word 文件。  
  
 [範例 COM 類別](./example-com-class.md)  
 示範如何將 C# 類別公開為 COM 物件。  
  
## <a name="c-language-specification"></a>C# 語言規格  

如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)中的[基本概念](~/_csharplang/spec/unsafe-code.md)。 語言規格是 C# 語法及用法的限定來源。
  
## <a name="see-also"></a>請參閱

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [C# 程式設計指南](../index.md)
- [與 Unmanaged 程式碼互通](../../../framework/interop/index.md)
- [逐步解說：Office 程式設計](./walkthrough-office-programming.md)
