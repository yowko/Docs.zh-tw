---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614381"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>MemberDescriptor.Equals 的實作不正確

#### <a name="details"></a>詳細資料

<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> 方法的原始實作會比較正在比較之物件的兩個不同字串屬性：分類名稱與描述字串。 修正方法是比較第一個物件的 <xref:System.ComponentModel.MemberDescriptor.Category> 和第二個物件的 <xref:System.ComponentModel.MemberDescriptor.Category>，比較第一個物件的 <xref:System.ComponentModel.MemberDescriptor.Description> 和第二個物件的 <xref:System.ComponentModel.MemberDescriptor.Description>。

#### <a name="suggestion"></a>建議

如果您的應用程式相依於當描述項相等時有時會傳回 `false` 的 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType>，而且您的目標是 .NET Framework 4.6.2 版或更新版本，則有數個選項：

- 變更程式碼以在呼叫 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> 方法之外，手動比較 <xref:System.ComponentModel.MemberDescriptor.Category> 和 <xref:System.ComponentModel.MemberDescriptor.Description> 欄位。
- 在 app.config 檔案中新增下列值，選擇不進行這項變更：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

如果您的應用程式目標設為 .NET Framework 4.6.1 或較舊版本，但在 .NET Framework 4.6.2 或更新版本上執行，而您想要啟用這項變更，您可以在 app.config 檔案中新增下列值，將相容性參數設為 `false`：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>
