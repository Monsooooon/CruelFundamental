# 什么是哈希树(Merkle Tree)？

哈希树（hash tree；Merkle tree），在密码学及计算机科学中是一种树形数据结构，每个叶节点均以数据块的哈希作为标签，而除了叶节点以外的节点则以其子节点标签的加密哈希作为标签 。哈希树能够高效、安全地验证大型数据结构的内容，是哈希链的推广形式。

哈希树中，哈希值的求取通常使用诸如SHA-2的加密哈希函数，但如果只是用于防止非故意的数据破坏，也可以使用不安全的校验和获取，比如CRC。

哈希树的顶部为顶部哈希（top hash），亦称根哈希（root hash）或主哈希（master hash）。以从 P2P 网络下载文件为例：通常先从可信的来源获取顶部哈希，如朋友告知、网站分享等。得到顶部哈希后，则整棵哈希树就可以通过 P2P 网络中的非受信来源获取。下载得到哈希树后，即可根据可信的顶部哈希对其进行校验，验证数据是否完整、是否遭受破坏。