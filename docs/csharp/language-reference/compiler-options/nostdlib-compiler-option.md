---
title: -nostdlib (C# 編譯器選項)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345083"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# 編譯器選項)

**-nostdlib** 會導致無法匯入 mscorlib.dll，而此檔案定義整個系統命名空間。

## <a name="syntax"></a>語法

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>備註

如果您想要定義或建立自己的系統命名空間和物件，請使用此選項。

若您沒有指定 **-nostdlib**，mscorlib.dll 會匯入您的程式中 (與指定 **-nostdlib-** 相同)。 指定 **-nostdlib** 等同於指定 **-nostdlib+**。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

> [!NOTE]
> 下列指示僅適用於 Visual Studio 2015 (及更早版本)。 在較新版本的 Visual Studio 中不存在**不引用 mscorlib.dll**生成屬性。

1. 開啟專案的 [屬性] **** 頁面。

2. 按一下 [建置] **** 屬性頁面。

3. 按一下 [進階]**** 按鈕。

4. 修改 [不要參考 mscorlib.dll] **** 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>。

## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](./index.md)
