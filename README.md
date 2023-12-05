# sublinks-js-client
A Javascript/Typescript client to interact with Sublinks.

Can act as a drop-in replacement for `lemmy-js-client` if app developers want to port their Lemmy clients to Sublinks.

Currently, all `lemmy-js-client` methods are simply wrapped, and all of its types are re-exported.  

As the native Sublinks API is developed, new methods and types will be added to this library to access those.  As the native API matures, methods will be ported over and the `lemmy-js-client` eventually phased out and removed as a dependency.

This client may also gain additional convenience methods for the Lemmy JS client, so even if you're developing for that platform, you may find this library useful.


### Example

```
import { 
    type GetSiteResponse,
    SublinksClient 
} from 'sublinks-js-client'

let site: GetSiteResponse | undefined

const client = new SublinksClient('sublinks.example.com');
try {
    let { jwt }  = await client.login({
        username_or_email: 'TestUser',
        password: '$uperS3cre+P@$sw0rd!'
    })

    client.setHeaders(
        {
            "Authorization": `Bearer ${jwt}`
        }
    )
}
catch (err) {
    console.log(err)
}

site = await client.getSite(); 
if (site) console.log(site)
```

