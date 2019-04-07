# iOSECID

# ecid 
   ecid 是iOS 设备非常低层的唯一识别号，用来识别芯片的。 或者说是CPU的唯一ID。 该ID 的计算过程非常简单， 因无法调试iboot， 只能给大概算法
   1. cpu 将一些有用数据映射到内存的一个固定地址， 这个时候kernel还没拉起来。
   2. 这个区块包含了cpu 的 晶元批次编号， 晶元编号， 以及晶元上的一个x,y,h 这么个东西。
   3. 将这几个串起来，就得到了唯一的ecid
# kernel 怎么撸的
   1. kernel 可以通过内存映射重新算一次。 如果那个区域还在的话
   2. iboot直接将参数传给kernel，然后注册到device tree
# kernel ext 怎么弄
   简单粗暴的可以通过IORegistery 在树上找这个unique-chip-id 
# 应用层怎么弄
   在不受权限影响的情况下， 通过IOKit的device tree 也能遍历到。 或者更上层的MGCopyAnswer函数得到。
