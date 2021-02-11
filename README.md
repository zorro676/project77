class Board(models.Model):
    name = models.charField(max_length=50, unique=True)
    description =  models.charField(max_length=200)

class Topic(models.Model):
    subject =models.charField(max_length=200)
    created_by =models.Foreignkey(User,related_name = 'topics',on_delete=models.CASCADE)
    board = models.Foreignkey(Board, related_name='topics',on_delete=models.CASCADE)
    created_dt = models.DateTimeField(auto_now_add=true)

class Post(models.Model):
    massage= models.TextField(max_length=4000)
    topic = models.Foreignkey(Topic,related_name ='posts',on_delete=models.CASCADE)
    created_by =models.Foreignkey(User,related_name = 'posts',on_delete=models.CASCADE)
    created_dt = models.DateTimeField(auto_now_add=true)
