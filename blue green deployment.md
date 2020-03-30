<h1 align="center">Blue-Green Deployment</h1>

Mavi-yeşil dağıtım yaklaşımı için mümkün olduğunca özdeş iki üretim ortamımız olmasını sağlayabiliriz. <br>
Herhangi bir zamanda, örneğimiz için diyelim ki mavi canlıya aldığımız ortam ve yeşil de test ortamımız olsun. 
Yazılımımızın yeni bir sürümünü hazırlarken, yeşil ortamda testin son aşamasını gerçekleştirebiliriz.<br> 
Yani yazılım yeşil ortamda çalıştıktan sonra, gelen tüm isteklerin yeşil ortama geçmesi için yönlendiriciyi değiştirip - mavi yani canlıdaki ortamımızın artık boşta kalması sağlanır.<br>
Mavi-yeşil dağıtım bize geri dönüş için hızlı bir yol sağlar - bir sorun olursa yönlendiriciyi mavi ortamımıza geri döndürebiliriz.<br>
İki ortamın farklı ancak olabildiğince özdeş olması gerekir. 
Yeşil ortamımızı canlı hale getirdikten ve kararlılığından memnun olduğumuzda, sonraki dağıtımımız için son test adımında mavi ortamı test ortamımız olarak kullanabiliriz.<br>
Bir sonraki sürümümüz için hazır olduğumuzda, daha önce maviden yeşile geçiş yaptığınmz şekilde yeşilden maviye geçebiliriz. Bu şekilde hem yeşil hem de mavi ortamları düzenli olarak canlı, önceki sürüm (geri alma için) ve sonraki sürüm için aralarında geçiş yapabiliriz.<br>
Temel fikir, geçiş yapmak için kolayca değiştirilebilen iki ortama sahip olmaktır. 

> Kaynak: https://www.martinfowler.com/bliki/BlueGreenDeployment.html
