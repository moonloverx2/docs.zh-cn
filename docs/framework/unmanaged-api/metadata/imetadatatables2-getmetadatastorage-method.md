---
title: "IMetaDataTables2::GetMetaDataStorage 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables2.GetMetaDataStorage
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b86542a55c0b4e778dfd956961f5a14a1c9d6f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="f1796-102">IMetaDataTables2::GetMetaDataStorage 方法</span><span class="sxs-lookup"><span data-stu-id="f1796-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="f1796-103">获取的大小和存储在指定的节中的元数据的内容。</span><span class="sxs-lookup"><span data-stu-id="f1796-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1796-104">语法</span><span class="sxs-lookup"><span data-stu-id="f1796-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1796-105">参数</span><span class="sxs-lookup"><span data-stu-id="f1796-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="f1796-106">[在中，out]指向元数据部分的指针。</span><span class="sxs-lookup"><span data-stu-id="f1796-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="f1796-107">[out]元数据流的大小。</span><span class="sxs-lookup"><span data-stu-id="f1796-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1796-108">要求</span><span class="sxs-lookup"><span data-stu-id="f1796-108">Requirements</span></span>  
 <span data-ttu-id="f1796-109">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1796-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1796-110">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1796-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1796-111">**库：**用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="f1796-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1796-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1796-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1796-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1796-113">See Also</span></span>  
 [<span data-ttu-id="f1796-114">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="f1796-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [<span data-ttu-id="f1796-115">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="f1796-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)