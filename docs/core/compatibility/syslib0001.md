---
title: SYSLIB0001 警告
description: 瞭解產生編譯時期警告 SYSLIB0001 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: d275717e22b260d9ceff4fe94993e9a0e6996cf0
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437838"
---
# <a name="syslib0001-the-utf-7-encoding-is-insecure"></a>SYSLIB0001：不安全的 UTF-7 編碼

UTF-7 編碼不再廣泛使用於應用程式，而許多規格現在禁止在交換中 [使用](https://security.stackexchange.com/a/68609/3573) 。 有時也會在不預期遇到 UTF-7 編碼資料的應用程式中， [用來做為攻擊向量](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) 。 Microsoft 會警告您使用， <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> 因為它不會提供錯誤偵測。

因此，下列 Api 會標示為已淘汰，從 .NET 5.0 開始。 使用這些 Api `SYSLIB0001` 時，會在編譯時期產生警告。

- <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 屬性
- <xref:System.Text.UTF7Encoding.%23ctor%2A> 構造 函數

## <a name="workarounds"></a>因應措施

- 如果您使用 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 的是或 <xref:System.Text.UTF7Encoding> 在自己的通訊協定或檔案格式內：

  切換為使用 <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> 或 <xref:System.Text.UTF8Encoding> 。 UTF-8 是業界標準，可廣泛地跨語言、作業系統和執行時間支援。 使用 UTF-8 可簡化未來的程式碼維護，讓它能夠與其余的生態系統更互通。

- 如果您要比較 <xref:System.Text.Encoding> 實例與 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ：

  相反地，請考慮針對已知的 UTF-7 字碼頁執行檢查，也就是 `65000` 。 藉由與字碼頁比較，您可以避免出現警告，也會處理一些邊緣案例，例如，如果有人呼叫 `new UTF7Encoding()` 或子類別化型別。

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>另請參閱

- [UTF-7 程式碼路徑已過時](core-libraries/5.0/utf-7-code-paths-obsolete.md)
