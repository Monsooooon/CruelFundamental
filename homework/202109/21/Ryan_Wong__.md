# K8S舍弃docker #
因为K8S本身并未就docker进行标准设定，它的对外接口不能直接用于docker，而是通过中间件使得docker能够作为其自身的运行时。当时采用docker也是本着使用现成轮子的思想。  
带来的缺点是，除了K8S本身所需的隔离、沙盘功能之外，docker的其他不必要的功能——比如联机、存储——也一并在K8S中运行，既降低性能也带来安全隐患。  
据了解，目前K8S只是不再对链接docker的中间件进行后续维护，老客户依然能在已部署了docker的环境内运行工作，也可以选择升级到符合K8S标准接口的环境来运行。