# react-adal
Azure Active Directory (ADAL) support for ReactJS

```
npm install react-adal
```

index.js

```javascript

import App from './App';
import { runWithAdal } from 'react-adal';
import { authContext } from './adalConfig';

runWithAdal(authContext, () => {

  ReactDOM.render(
    <Provider store={store}>
      <App />
    </Provider>,
    document.getElementById('root'),
  );

});

```

adalConfig.js

```javascript

import { AuthenticationContext, adalGetToken, adalFetch } from 'react-adal';

export const adalConfig = {
  tenant: '14d71d65-f596-4eae-be30-27f079bf8d4b',
  clientId: '14d71d65-f596-4eae-be30-27f079bf8d4b',
  endpoints: {
    api: '14d71d65-f596-4eae-be30-27f079bf8d4b',
  },
  cacheLocation: 'localStorage',
};

export const authContext = new AuthenticationContext(adalConfig);

export const adalApiFetch = (fetch, url, options) =>
  adalFetch(authContext, adalConfig.endpoints.api, fetch, url, options);


```

use adalApiFetch with your favorite "fetch" in your api call.

That's all.

Enjoy!