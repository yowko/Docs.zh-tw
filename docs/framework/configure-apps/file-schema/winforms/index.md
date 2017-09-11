---
title: "Windows Form 組態區段 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: dedf9497a684c4b11f84b60de21ec73b563c6d19
ms.contentlocale: zh-tw
ms.lasthandoff: 05/03/2017

---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="aa063-102">Windows Form 組態區段</span><span class="sxs-lookup"><span data-stu-id="aa063-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="aa063-103">Windows Forms 組態設定允許 Windows Forms 應用程式儲存並擷取有關自訂應用程式設定 (例如多重監視器支援、高 DPI 支援，以及其他預先定義的組態設定) 的資訊。</span><span class="sxs-lookup"><span data-stu-id="aa063-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="aa063-104">Windows Forms 應用程式組態設定是儲存在應用程式組態檔的 `System.Windows.Forms.ConfigurationSection` 元素中。</span><span class="sxs-lookup"><span data-stu-id="aa063-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa063-105">語法</span><span class="sxs-lookup"><span data-stu-id="aa063-105">Syntax</span></span>

```xml
<configuration>
  \<System.Windows.Forms.ConfigurationSection>
  ...
  \</System.Windows.Forms.ConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa063-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="aa063-106">Attributes and elements</span></span>

<span data-ttu-id="aa063-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aa063-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa063-108">屬性</span><span class="sxs-lookup"><span data-stu-id="aa063-108">Attributes</span></span>

<span data-ttu-id="aa063-109">無。</span><span class="sxs-lookup"><span data-stu-id="aa063-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa063-110">子元素</span><span class="sxs-lookup"><span data-stu-id="aa063-110">Child elements</span></span>

<span data-ttu-id="aa063-111">元素</span><span class="sxs-lookup"><span data-stu-id="aa063-111">Element</span></span>  |<span data-ttu-id="aa063-112">說明</span><span class="sxs-lookup"><span data-stu-id="aa063-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="aa063-113">新增具有指定值的組態設定金鑰</span><span class="sxs-lookup"><span data-stu-id="aa063-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="aa063-114">父元素</span><span class="sxs-lookup"><span data-stu-id="aa063-114">Parent elements</span></span>

<span data-ttu-id="aa063-115">元素</span><span class="sxs-lookup"><span data-stu-id="aa063-115">Element</span></span>  |<span data-ttu-id="aa063-116">說明</span><span class="sxs-lookup"><span data-stu-id="aa063-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="aa063-117">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aa063-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="aa063-118">通用語言執行平台和 Windows Forms 應用程式所使用之每個組態檔中的根元素</span><span class="sxs-lookup"><span data-stu-id="aa063-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="aa063-119">備註</span><span class="sxs-lookup"><span data-stu-id="aa063-119">Remarks</span></span>

<span data-ttu-id="aa063-120">從 .NET Framework 4.7 開始，`<System.Windows.Forms.ConfigurationSection>` 元素能允許您設定 Windows Forms 應用程式，以利用 .NET Framework 最新版本中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="aa063-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="aa063-121">`<System.Windows.Forms.ConfigurationSection>` 元素可以包含一或多個子 [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) 元素，每個子元素都能定義一個特定的組態設定。</span><span class="sxs-lookup"><span data-stu-id="aa063-121">The `<System.Windows.Forms.ConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa063-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa063-122">See also</span></span>

<span data-ttu-id="aa063-123">[組態檔結構描述](../index.md)
[Windows Forms 中的高 DPI 支援](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="aa063-123">[Configuration File Schema](../index.md)
[High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)</span></span>

