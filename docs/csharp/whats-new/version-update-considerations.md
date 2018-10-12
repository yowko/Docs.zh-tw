---
title: 適用於 C# 開發人員的版本和更新考量
description: 在您的程式庫中引進新的語言功能，會影響使用該程式庫的程式碼。
ms.date: 09/19/2018
ms.openlocfilehash: 56685422e2c73dcca25acbdccb3a77a8de9df775
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199927"
---
# <a name="version-and-update-considerations-for-c-developers"></a>適用於 C# 開發人員的版本和更新考量

將新功能新增至 C# 語言時，相容性是非常重要的目標。 在幾乎所有情況下，現有程式碼可以使用新的編譯器版本重新編譯，不會有任何問題。

當您在程式庫中採用新語言功能時，可能需要更加小心。 您可能會使用最新版本中的功能來建立新程式庫，並需要確保使用舊版編譯器建置的應用程式可以使用它。 或者您可能升級了現有的程式庫，但是您的許多使用者都還沒有升級的版本。 當您決定採用新功能時，需要考慮兩個相容性變化：來源相容及二進位相容。

## <a name="binary-compatible-changes"></a>二進位相容變更

如果您更新了程式庫，而且不需要重建使用此程式庫的應用程式和程式庫就能開始使用，則您程式庫上的這些變更屬於**二進位相容**。 相依組件並不需要重建，也不需要任何原始程式碼變更。 二進位相容變更也是來源相容變更。

## <a name="source-compatible-changes"></a>來源相容變更

如果使用您程式庫的應用程式和程式庫不需要變更原始程式碼，但來源必須根據新版本重新編譯，才能正常運作，則您程式庫上的這些變更屬於**來源相容**。

## <a name="incompatible-changes"></a>不相容變更

如果變更既不是**來源相容**也不是**二進位相容**，則相依程式庫和應用程式需要變更原始程式碼與重新編譯。

## <a name="evaluate-your-library"></a>評估您的程式庫

這些相容性概念會影響您程式庫中的公用和受保護宣告，但不會影響其內部實作。 在內部採用任何新的功能都是**二進位相容**。  

**二進位相容**變更會提供新語法，該語法會針對公用宣告產生與舊語法相同的編譯程式碼。 例如，將方法變更為運算式主體成員是**二進位相容**變更：

原始程式碼：

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

新程式碼：

```csharp
public double CalculateSquare(double value) => value * value;
```

**來源相容**變更會引進語法，該語法會變更公用成員的已編譯程式碼，但是會使用與現有呼叫網站相容的方式。 例如，將方法簽章從「依值 (by value)」參數變更為 `in`「依參考 (by reference)」參數是來源相容，而不是二進位相容：

原始程式碼：

```csharp
public double CalculateSquare(double value) => value * value;
```

新程式碼：

```csharp
public double CalculateSquare(in double value) => value * value;
```

[最新功能](index.md)文章中會註明影響公用宣告的引進功能是來源相容或二進位相容。