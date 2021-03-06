[Home](../readme.md "Home")

#### SECTION 5
----
## Challenges that Agile Toolkit solves

Agile Toolkit framework is not there only for a show. It is there to solve a real-life challenges a typical web developer is facing.

### Secure by Design

How do you force your developer to produce secure software? One way would be to send him to several security conferences and lectures or even hire a hacker to review the code for a possible faults.

Agile Toolkit introduces the concept of “Secure by Design”. It is a technique designed to create a simpler way which is also a simple way.

Majority of security problems arise from the lack of encoding as the content goes from one system to another. SQL databases controlled through a language constructed by string concatenation often is a source of many security issues.

The similar problem does not appear in noSQL databases which have object-oriented interaction techniques. Agile Toolkit introduces a object-oriented technique for interacting with SQL, JavaScript and HTML which is secure by default.

    $ops = $_GET['arg'];
    $this->add('H1')->set($ops);
    $this->add('Button')->js('click')->univ()->alert($ops);
    $this->api->dsql()
        ->table('user')->where('name',$ops)->delete();

It might seem that the above code contain several vulnerabilities - JavaScript injection and SQL injection. However it's perfectly safe in Agile Toolkit. While it is advisable to validate the input data in Agile Toolkit, the way how developer interacts with HTML, JavaScript or SQL contains a proper escaping and pretty much eliminates any possible vulnerabilities without developer even being aware of them.

### Secure Model Design

Models describe business entities in the database. For most of us RDBMS is a database of choice and while NoSQL solutions can be helpful sometimes, the SQL is used in majority of software projects.

To simplify interaction with the database there are two abstraction mechanisms in Agile Toolkit: Active Record and Dynamic SQL. Their combination brings the implementation of “Relational Models”.

If you are familiar with "Views" in several SQL implementation, this is quite similar to models in Agile Toolkit. Model can select either all records from a SQL table or a sub-set limited by certain conditions. It can also interact with multiple tables simultaneously through joins or expressions.

The aspect of security is added by a sticky conditions. Once condition is applied to the model, the condition can no longer be removed. For example, if you set the following condition to your model

    $model->addCondition('deleted',false);
    
then all the further interaction with the model will only affect records which are not flagged as deleted:

    $model->load(5);    // will not delete deleted entry
    
    $model->set('deleted',true)->save(); // will not save
    
    foreach($model as $row){}    // will skip deleted entries
    
    $cnt=$model->count()->getOne(); // will not count deleted
    
    $model->dsql()->set('name',123)
        ->update(); // will not update deleted entries

### Scalability by Design

Many software platforms offer you a unique, interesting and even magical new ways of building web software, but as your logic becomes more and more complex, the performance start to crumble. Other frameworks could not carry less about performance and scalability of your software leaving it all in the hands of developer.

Agile Toolkit offers developer a ways how to keep their software incredibly scalable even as the data model becomes more and more complex. Consider this example:

    // Count states from user addresses
    $states=array();
    foreach($user_model as $r){
        $address_model=$user_model->ref('address_id');
        $states[$address_model['state']]++;
    }
This syntax is common in many Active-Record implementation. Traversing from the “user” model to the relevant “address” model executes one more query and the whole code generates N+1 queries and is highly ineffective.

Few of Active-Record implementation allow you to implement it by creating a separate model. Other implementation require you to come up with a query yourself. Agile Toolkit allows you to tweak the model just for a specific query:

    // Count states from user addresses
    $states=array();
    $user_model->join('address')->addField('state');
    foreach($user_model as $r){
        $states[$user_model['state']]++;
    }
The new approach will perform only a single query. There are many other ways to achieve the above in the single query with Agile Toolkit.

###Reusable by Design

CRUD is a component present in many frameworks. Short for Create, Read, Update and Delete this component allows building a simple administrative interface for managing model data.

More often than not CRUD is a generator - a new excuse for avoiding “Don't Repeat Yourself ” principle. Once you generate pages, you would then need to edit those pages yourself if you wish to change anything.

In Agile Toolkit CRUD is a View which heavily rely on Form and Grid views. While CRUD does offer some of the functionality, as a developer you can still access the Grid / Form components and modify them to your liking.

----

<center>**In Agile Toolkit there are no Code Generation**</center>

----

So how do you add a new button / action to a standard CRUD in Agile Toolkit?

    $crud=$page->add('CRUD');
    $crud->setModel('User');
    if($crud->grid){
        $crud->grid->addColumn('button','test');
        if($_GET['test']){
            $this->js()->univ()->alert('Testing: '.
                $crud->model
                    ->load($_GET['test'])
                    ->get('name')
        }
    }
    
In fact, many other complex controls and admins are in fact views which you can extend, redefine and interact with their elements directly. As you will develop your projects, you will also create re-usable components on a daily basis.

With just a few simple modifications any component in your code can be converted into add-on and published for others to use.

### Collaborative by Design

Have you ever worked on as software project within a team? Have you ever found a code added by other developer in your files which was breaking some of your functionality? This happens often, but not in Agile Toolkit.

When you develop project in Agile Toolkit, you clearly separate things. For example you might have a dashboard page containing all sorts of views on them: recent purchases, account balance, current offer and advertisement block. Your dashboard page would most likely look like this:

[Chapter 2](../chapter2/intro.md "Chapter 2")