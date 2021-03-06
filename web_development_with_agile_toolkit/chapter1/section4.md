[Home](../readme.md "Home")

#### SECTION 4
----
## Depth of Functionality

No doubt that many of you would look at the simple functionality of Agile Toolkit and will assume it's a basic framework. In reality Agile Toolkit uses a lot of sophisticated logic to make it tick in the best possible way.

Let's draw some lines between Laravel's Fluent Query Builder and Agile Toolkit's DSQL. On the surface they appear to be quite similar:

    // Laravel
    $users = DB::table('users')
        ->where('email', '=', 'example@gmail.com')
        ->where_in('id', array(1, 2, 3))
        ->get();
    
    // DSQL
    $this->api->db->dsql()->table('users')
        ->where('email','=','example@gmail.com')
        ->where('id','in',array(1, 2, 3))
        ->get();

However both query builders are on completely different levels. DSQL is template-based recursive on-demand renderer while Fluent builds query as-you-define it. Here are some of the things DSQL does and Fluent does not: Support for subqueries; Recursive rendering; Custom class design; Modifying existing query; Native integration with Model Fields.

Because of design decisions in DSQL, it's possible to have a very fluid and dynamic Model / ORM implementation on top of it. Having said that, the implementations of both query builders is quite similar.

[Next Section](section5.md "Next Section")