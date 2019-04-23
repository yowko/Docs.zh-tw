---
title: .NET Security Analyzer - .NET
description: 了解如何使用 .NET Framework Analyzers 套件中的 .NET Security Analyzer 來尋找和解決安全性風險
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: cbd9bcdb12a423f54aa4ff82d88f07c20023c48f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769459"
---
# <a name="the-net-framework-analyzer"></a>.NET Framework Analyzer

您可以使用 .NET Framework Analyzer 來尋找 .NET Framework 應用程式碼中的潛在問題。 此分析器會找出潛在問題並建議其修正程式。

當您撰寫程式碼時，或在 CI 組建期間，分析器會以互動方式在 Visual Studio 中執行。 您應該盡早在開發中將分析器新增至專案。 在程式碼中找到任何潛在問題的速度愈快，修正就愈容易。 不過，您可以在開發週期的任何時間新增它。 它會找到現有程式碼的任何問題，並在您持續開發時警告您發生新問題。

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>安裝和設定 .NET Framework Analyzer

.NET Security Analyzer 在您想要執行它們的每個專案上，都必須安裝為 NuGet 套件。 只有一位開發人員必須將它們新增至專案。 分析器套件是一種專案相依性，而且會在具有已更新方案之後，於每位開發人員的電腦上執行。

[Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet 套件提供 .NET Framework Analyzer。 此套件只提供 .NET Framework 特有的分析器，包含安全性分析器。 在大部分情況下，您會想要有 [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 套件。 FxCopAnalyzers 彙總套件包含 Framework.Analyzers 套件中所含的所有架構分析器以及下列分析器：
- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers) \(英文\)：提供一般指導方針和 .NET Standard API 指導方針
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers)\(英文\) ：提供 .NET Core API 專屬的分析器。
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers) \(英文\)：提供包含為程式碼之文字的指導方針，包含註解。

若要進行安裝，請以滑鼠右鍵按一下專案，然後選取 [管理相依性]。
從 NuGet 總管中，搜尋 "NetFramework Analyzer" 或視需要搜尋 "Fx Cop Analyzer"。 在您方案的所有專案中安裝最新穩定版本。

## <a name="using-the-net-framework-analyzer"></a>使用 .NET Framework Analyzer

安裝 NuGet 套件之後，請建置方案。 分析器將會報告它在您的程式碼基底中找到的任何問題。 在 Visual Studio [錯誤清單] 視窗中，這些問題回報為警告，如下圖所示：

![架構分析器回報的問題](./media/framework-analyzers-2.png)

當您撰寫程式碼時，會在程式碼的任何潛在問題下方看到曲線。
將游標暫留在任何問題上，就會看到該問題的詳細資料，以及任何可能修正程式的建議，如下圖所示：

![架構分析器所找到的互動式問題報表](./media/framework-analyzers-1.png)

分析器會檢查您方案中的程式碼，並提供所有這些問題的警告清單：

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058:類型不應該擴充特定基底類型

您不應該直接衍生自 .NET Framework 中的少數類型。 

**分類：** 設計

**嚴重性：** 警告

其他資訊：[CA:1058：類型不應該擴充特定基底類型](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153:請勿擷取損毀狀態例外狀況

攔截損毀狀態例外可能會遮罩錯誤 (例如存取違規)，導致不一致的執行狀態，或讓攻擊者更容易危害系統。 相反地，會攔截並處理一組更具體的例外狀況類型，或重新擲回例外狀況

**分類：** 安全性

**嚴重性：** 警告

其他資訊：[## CA2153：請勿擷取損毀狀態例外狀況](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229:必須實作序列化建構函式

當您建立可實作 <xref:System.Runtime.Serialization.ISerializable> 介面但未定義必要序列化建構函式的類型時，分析器會產生這個警告。 若要修正此規則的違規情形，請實作序列化建構函式。 針對密封類別，讓建構函式成為 private，否則為 protected。 序列化建構函式具有下列簽章：

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

**分類：** 使用量

**嚴重性：** 警告

其他資訊：[CA2229：必須實作序列化建構函式](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235:必須標記所有不可序列化的欄位

可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。 您必須明確地以 <xref:System.NonSerializedAttribute> 標記該欄位，來修正這個警告。

**分類：** 使用量

**嚴重性：** 警告

其他資訊：[CA2235：必須標記所有不可序列化的欄位](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237:以可序列化標記 ISerializable 類型

若要讓通用語言執行平台辨識為可序列化，即使類型透過實作 <xref:System.Runtime.Serialization.ISerializable> 介面來使用自訂序列化常式，仍然必須使用 <xref:System.SerializableAttribute> 屬性來標記類型。

**分類：** 使用量

**嚴重性：** 警告

其他資訊：[CA2237：ISerializable 型別必須標記 serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075:XML 中不安全的 DTD 處理

如果您使用不安全的 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> 執行個體或參考外部實體來源，剖析器可能會接受未受信任的輸入，而將機密資訊洩漏給攻擊者。  

**分類：** 安全性

**嚴重性：** 警告

其他資訊：[A3075：XML 中不安全的 DTD 處理](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350：請勿使用弱式密碼編譯演算法

攻擊變得更為進階時，密碼編譯演算法的強度會在一段時間後下降。 根據此密碼編譯演算法的類型和應用程式，其密碼編譯強度的進一步下降可能可讓攻擊者讀取已譯成密碼的訊息、竄改已譯成密碼的訊息、偽造數位簽章、竄改雜湊內容，或根據此演算法洩露任何加密系統。 針對加密，使用金鑰長度大於或等於 128 位元的 AES 演算法 (可接受 AES-256、AES-192 和 AES-128)。 針對雜湊，在 SHA-2 系列 (例如 SHA-2 512、SHA-2 384 或 SHA-2 256) 中使用雜湊函式。

**分類：** 安全性

**嚴重性：** 警告

其他資訊：[CA5350：請勿使用弱式密碼編譯演算法](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351：請勿使用損壞的密碼編譯演算法

具有可透過運算方式中斷這個演算法的攻擊。 這可讓攻擊者中斷設計成提供的密碼編譯保證。 根據此密碼編譯演算法的類型和應用程式，這可能可讓攻擊者讀取已譯成密碼的訊息、竄改已譯成密碼的訊息、偽造數位簽章、竄改雜湊內容，或根據此演算法洩露任何加密系統。 針對加密，使用金鑰長度大於或等於 128 位元的 AES 演算法 (可接受 AES-256、AES-192 和 AES-128)。 針對雜湊，在 SHA-2 系列 (例如 SHA512、SHA384 或 SHA256) 中使用雜湊函式。 針對數位簽章，使用金鑰長度大於或等於 2048 位元的 RSA，或金鑰長度大於或等於 256 位元的 ECDSA。

**分類：** 安全性

**嚴重性：** 警告

其他資訊：[CA5351：請勿使用損壞的密碼編譯演算法](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)
