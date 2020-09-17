---
title: 在 .NET 中執行自訂設定提供者
description: 瞭解如何在 .NET 應用程式中執行自訂設定提供者。
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: how-to
ms.openlocfilehash: 968bf202eeea32742444681260d5ab0b27b403f9
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720746"
---
# <a name="implement-a-custom-configuration-provider-in-net"></a>在 .NET 中執行自訂設定提供者

有許多設定 [提供者](configuration-providers.md) 可用於一般設定來源，例如 JSON、XML 和 INI 檔案。 當其中一個可用的提供者不符合您的應用程式需求時，您可能需要執行自訂設定提供者。 在本文中，您將瞭解如何執行依賴資料庫做為其設定來源的自訂設定提供者。

## <a name="custom-configuration-provider"></a>自訂設定提供者

範例應用程式示範如何建立基本的設定提供者，以使用 [Entity Framework (EF) Core](/ef/core)，從資料庫讀取設定機碼值組。

提供者具有下列特性：

- EF 記憶體內資料庫會用於示範用途。 若要使用需要連接字串的資料庫，請實作第二個 `ConfigurationBuilder` 以從另一個設定提供者提供連接字串。
- 啟動時，該提供者會將資料庫資料表讀入到設定中。 該提供者不會以個別機碼為基礎查詢資料庫。
- 未實作變更時重新載入，因此在應用程式啟動後更新資料庫對應用程式設定沒有影響。

定義 `Settings` 記錄類型實體，以將設定值儲存在資料庫中。 例如，您可以在 [*模型*] 資料夾中新增*Settings.cs*檔案：

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

如需記錄類型的詳細資訊，請參閱 [c # 9 中的記錄類型](../../csharp/whats-new/csharp-9.md#record-types)。

新增 `EntityConfigurationContext` 以存放及存取已設定的值。

*Provider/EntityConfigurationCoNtext .cs*：

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

建立會實作 <xref:Microsoft.Extensions.Configuration.IConfigurationSource> 的類別。

*Provider/EntityConfigurationSource .cs*：

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

透過繼承自 <xref:Microsoft.Extensions.Configuration.ConfigurationProvider> 來建立自訂設定提供者。 若資料庫是空的，設定提供者會初始化資料庫。 由於設定索引鍵不區分大小寫，因此用來初始化資料庫的字典會以不區分大小寫的比較子來建立 ([stringcomparison. OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)) 。

*Provider/EntityConfigurationProvider .cs*：

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

`AddEntityConfiguration`擴充方法允許將設定來源加入至 <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> 實例。

*Extensions/ConfigurationBuilderExtensions .cs*：

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

下列程式碼顯示如何在 *Program.cs* 中使用自訂 `EntityConfigurationProvider`：

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="21-22":::

## <a name="see-also"></a>另請參閱

- [.NET 中的設定](configuration.md)
- [.NET 中的設定提供者](configuration-providers.md)
