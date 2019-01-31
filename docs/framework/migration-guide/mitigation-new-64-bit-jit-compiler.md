---
title: 風險降低：新的 64 位元 JIT 編譯器
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d3eb82cf9bac1e40947fb78882d18c5f09b0092
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690081"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>風險降低：新的 64 位元 JIT 編譯器
從 .NET Framework 4.6 開始，執行階段包含新的 64 位元 JIT 編譯器，用於 Just-In-Time 編譯。 這項變更不會影響使用 32 位元 JIT 編譯器的編譯。  
  
## <a name="unexpected-behavior-or-exceptions"></a>未預期的行為或例外狀況  
 在某些情況下，使用新版 64 位元 JIT 編譯器的編譯會產生執行階段例外狀況，或是產生在執行舊版 64 位元 JIT 編譯器所編譯的程式碼時未觀察到的行為。 下列是已知的差異︰  
  
> [!IMPORTANT]
>  上述所有已知問題都已在隨 .NET Framework 4.6.2 發行的新版 64 位元編譯器中解決。 大部分問題已在隨附於 Windows Update 的 .NET Framework 4.6 和 4.6.1 服務版本中解決。 將您的 Windows 版本更新至最新版或升級至 .NET Framework 4.6.2，即可解決這些問題。  
  
-   在某些情況下，已開啟最佳化的發行組建中的 Unboxing 作業可能會擲回 <xref:System.NullReferenceException>。  
  
-   在某些情況下，執行大型方法主體中的實際執行程式碼可能會擲回 <xref:System.StackOverflowException>。  
  
-   某些狀況下，發行組建中傳遞至方法的結構會被視為參考型別而非實值型別。 這個問題的其中一種表現，就是集合中的個別項目會以非預期的順序出現。  
  
-   在某些情況下，如果啟用最佳化，<xref:System.UInt16> 的值在設定高位元時的比較會不正確。  
  
-   在某些情況下，尤其是初始化陣列值時，使用 <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL 指令初始化記憶體，可能會以不正確的值初始化記憶體。 這會造成未處理的例外狀況或不正確的輸出。  
  
-   在少數情況下，如果啟用編譯器最佳化，條件式位元測試可能會傳回不正確的 <xref:System.Boolean> 值或擲回例外狀況。  
  
-   某些狀況下，如果使用 `if` 陳述式在進入 `try` 區塊之前和自 `try` 區塊退出時測試某項條件，而且也在 `catch` 或 `finally` 區塊中評估該條件時，新版 64 位元 JIT 編譯器在最佳化程式碼時會將 `if` 條件自 `catch` 或 `finally` 區塊中移除。 因此，`catch` 或 `finally` 區塊的 `if` 陳述式中的程式碼會無條件執行。  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>降低已知問題的風險  
 如果您遇到上述問題，可以採取以下任一種方式來解決︰  
  
-   升級至 .NET Framework 4.6.2。 隨附於 .NET Framework 4.6.2 中的新版 64 位元編譯器可以解決這些已知問題。  
  
-   執行 Windows Update，確定您的 Windows 已更新至最新版本。 .NET Framework 4.6 和 4.6.1 的服務更新可解決上述問題中除了 Unboxing 作業之 <xref:System.NullReferenceException> 以外的所有問題。  
  
-   使用舊版 64 位元 JIT 編譯器編譯。 如需如何進行的詳細資訊，請參閱[降低其他問題的風險](#Other)一節。  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>降低其他問題的風險  
 如果舊版和新版 64 位元 JIT 編譯器編譯的程式碼之間有任何差異，或是使用新版 64 位元 JIT 編譯器編譯的應用程式偵錯版本和發行版本之間有任何差異，您可以使用舊版 64 位元 JIT 編譯器搭配下列方式來編譯應用程式：  
  
-   若以每一應用程式為基礎，您可以將 [\<useLegacyJIT>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) 項目新增至應用程式的組態檔。 下列程式碼會停止以新版 64 位元 JIT 編譯器進行編譯，改用舊版 64 位元 JIT 編譯器。  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   若以每一使用者為基礎，您可以將名為 `useLegacyJit` 的 `REG_DWORD` 值加入至登錄的 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 索引鍵。 值為 1 會啟用舊版 64 位元 JIT 編譯器；值為 0 會停用它，並啟用新版 64 位元 JIT 編譯器。  
  
-   若以每一電腦為基礎，您可以將名為 `useLegacyJit` 的 `REG_DWORD` 值加入至登錄的 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 索引鍵。 值為 1 會啟用舊版 64 位元 JIT 編譯器；值為 0 會停用它，並啟用新版 64 位元 JIT 編譯器。  
  
 您也可以前往 [Microsoft Connect](https://connect.microsoft.com/VisualStudio) 回報錯誤，讓我們知道問題所在。  
  
## <a name="see-also"></a>另請參閱
- [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
- [\<useLegacyJit> 項目](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
