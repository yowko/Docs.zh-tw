---
ms.openlocfilehash: 0237c848d71150aaea1f9de4f4b16a0cbbc4ab3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615621"
---
### <a name="new-64-bit-jit-compiler-in-the-net-framework-46"></a>.NET Framework 4.6 中的新 64 位元 JIT 編譯器

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6 開始，使用新的 64 位元 JIT 編譯器來進行 Just-In-Time 編譯。 在某些情況下，如果使用 32 位元編譯器或舊版 64 位元 JIT 編譯器來執行應用程式，則會擲回非預期的例外狀況或遵守不同的行為。 這種變更不會影響32位 JIT 編譯程式。 下列是已知的差異︰

- 在某些情況下，已開啟最佳化的發行組建中的 Unboxing 作業可能會擲回 <xref:System.NullReferenceException>。
- 在某些情況下，執行大型方法主體中的實際執行程式碼可能會擲回 <xref:System.StackOverflowException>。
- 某些狀況下，發行組建中傳遞至方法的結構會被視為參考型別而非實值型別。 這個問題的其中一種表現，就是集合中的個別項目會以非預期的順序出現。
- 在某些情況下，如果啟用最佳化，<xref:System.UInt16> 的值在設定高位元時的比較會不正確。
- 在某些情況下，尤其是初始化陣列值時，使用 <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL 指令初始化記憶體，可能會以不正確的值初始化記憶體。 這會造成未處理的例外狀況或不正確的輸出。
- 在少數情況下，如果啟用編譯器最佳化，條件式位元測試可能會傳回不正確的 <xref:System.Boolean> 值或擲回例外狀況。
- 某些狀況下，如果使用 `if` 陳述式在進入 `try` 區塊之前和自 `try` 區塊退出時測試某項條件，而且也在 `catch` 或 `finally` 區塊中評估該條件時，新版 64 位元 JIT 編譯器在最佳化程式碼時會將 `if` 條件自 `catch` 或 `finally` 區塊中移除。 因此，`catch` 或 `finally` 區塊的 `if` 陳述式中的程式碼會無條件執行。

#### <a name="suggestion"></a>建議

**降低已知問題的風險** <br/> 如果您遇到上述問題，可以採取以下任一種方式來解決︰

- 升級至 .NET Framework 4.6.2。 隨附於 .NET Framework 4.6.2 中的新版 64 位元編譯器可以解決這些已知問題。
- 執行 Windows Update，確定您的 Windows 已更新至最新版本。 .NET Framework 4.6 和 4.6.1 的服務更新可解決上述問題中除了 Unboxing 作業之 <xref:System.NullReferenceException> 以外的所有問題。
- 使用舊版 64 位元 JIT 編譯器編譯。 如需如何進行的詳細資訊，請參閱**降低其他問題的風險**一節。
**降低其他問題的風險** <br/> 如果舊版和新版 64 位元 JIT 編譯器編譯的程式碼之間有任何差異，或是使用新版 64 位元 JIT 編譯器編譯的應用程式偵錯版本和發行版本之間有任何差異，您可以使用舊版 64 位元 JIT 編譯器搭配下列方式來編譯應用程式：

- 以每個應用程式為基礎，您可以將 [<](~/docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) 元素新增至應用程式的設定檔。 下列程式碼會停止以新版 64 位元 JIT 編譯器進行編譯，改用舊版 64 位元 JIT 編譯器。

    ```xml
    <?xml version ="1.0"?>
    <configuration>
      <runtime>
       <useLegacyJit enabled="1" />
      </runtime>
    </configuration>
    ```

- 若以每一使用者為基礎，您可以將名為 `useLegacyJit` 的 `REG_DWORD` 值加入至登錄的 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 索引鍵。 值為 1 會啟用舊版 64 位元 JIT 編譯器；值為 0 會停用它，並啟用新版 64 位元 JIT 編譯器。
- 若以每一電腦為基礎，您可以將名為 `useLegacyJit` 的 `REG_DWORD` 值加入至登錄的 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 索引鍵。 值為 `1` 會啟用舊版 64 位元 JIT 編譯器；值為 `0` 會停用它，並啟用新版 64 位元 JIT 編譯器。
您也可以前往 [Microsoft Connect](https://connect.microsoft.com/VisualStudio) 回報錯誤，讓我們知道問題所在。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6         |
| 類型    | 正在重定目標 |
