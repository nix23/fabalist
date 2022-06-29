<div id="top"></div>

<!-- INTRO -->
<br />
<div align="center">
  <a href="img/1.jpg?raw=true">
    <p align="center">
      <img src="img/1.jpg" width="40%">
    </p>
  </a>

  <h3 align="center">Fabalist - website(Symfony,Jquery) + Ios/Android apps(React native) for food and beverage industry</h3>

  <p align="center">
    Fabalist - last project on which I have worked on for the last 6 years. During that period over 50000 resumes were sent using our services and about 20% of people got hired.
    I have successfully developed and maintained website as well as mobile apps. 
    Website: <a href="https://fabalist.com">Open</a>.
  </p>
</div>

<!-- WEBSITE FUNCTIONALITY SHORT OVERVIEW -->
## Website Functionality Short Overview

### Public area

* Landing page
* About Us page
* Contact Us page
* Restaurants page
* Restaurant profile page
* Restaurant job posting page
* Job seeker profile page

### Dashboard for admins

* Dashboard page
* Accounts page
* Last activity page
* Jobs page
* Resumes page
* Emails page
* etc...

### Dashboard for personal accounts (job seekers)

* Dashboard page
* Manage resume page
* Create resume page
* Setup job alert preferences page
* Favorite jobs page
* etc...

### Dashboard for business accounts (restaurant managers)

* Dashboard page
* Post job page
* View resume page
* Manage candidates page
* Manage team page
* Manage schedules page
* etc...

### How this functionality works together

Business accounts can post jobs - personal accounts can apply on those jobs.
In process of posting employer can select job category, title, description as well as other fields. Job is kept active for 7 days - after that its status becomes `inactive` and job seekers cannot apply on it anymore. Employers can add job seekers to contacts, mark them as candidates, start a chat with any of them, invite to interview or call them directly. Job seekers can upload file with a resume or create online with resume builder.

### 3-rd party integrations

* Mailgun to send / receive emails
* Stripe fixed payments for job postings
* Stripe subscriptions for unlimited job postings
* React-native-iap library for Apple/Google payments in mobile apps
* Facebook/Google/Apple/Linked in log in / sign up buttons

<!-- CODEBASE SHORT OVERVIEW -->
## Codebase Short Overview

### /

* docker-compose.yml structure (3 containers, used in dev env):
  ```sh
    services:
        web:
            ...
            container_name: web
        mysql:
            ...
            container_name: mysql
        php:
            ...
            container_name: php
  ```

* gulpfile.js structure:
  ```sh
    var app = {
        buildCss: function(paths, outputFilename) {
            // ...
        },
        buildJs: function(paths, outputFilename) {
            // ...
        }
    };

    // ...

    // Creating diff.types of css file builds.
    gulp.task('css', function() {
        pipe.add([c.clientBundleCss + "boot/" + c.sass], 'client-core');
        pipe.add(c.clientBundleCss + "views/aboutUs/" + c.sass, 'client-aboutus');
        pipe.add(c.clientBundleCss + "views/account/" + c.sass, 'client-account');
        // ...
        pipe.add([
            c.adminBundleCss + "vendor/" + c.sass,
            c.adminBundleCss + "vendor/" + c.css,
            c.adminBundleCss + "boot/" + c.sass
        ], 'admin-core');
        pipe.add(c.adminBundleCss + "views/" + c.sass, 'admin-views');

        pipe.run(app.buildCss);
    });

    // Creating diff.types of js file builds.
    gulp.task('js', function() {
        pipe.add([
            c.clientBundleJs + "vendor/" + c.js,
            c.clientBundleJs + "controller/" + c.js,
            c.clientBundleJs + "boot/" + c.js
        ], 'client-core');

        // Client modules
        pipe.add(c.clientBundleJs + "views/aboutUs/" + c.js, 'client-aboutus');
        pipe.add(c.clientBundleJs + "views/account/" + c.js, 'client-account');
        // ...

        pipe.run(app.buildJs);
    });
  ```

### /src/Ntech/CoreBundle/

Contains core services used by all other bundles.

* Structure:
  ```sh
    Command/
    DataFixtures/
    Entity/
        Account.php
        Notification.php
        ...
    Form/
        Type/
            AccountType.php
            BusinessAccountType.php
            PersonalAccountType.php
            ...
    Helpers/
    Repository/
        AccountRepository.php
        NotificationRepository.php
        ...
    Service/
        EmailManager.php
        Geocoder.php
        Mailer.php
        NotificationsManager.php
        Paginator.php
        StripeClient.php
        ...
    Twig/
    UploadController/
    Validator/
  ```

### /src/Ntech/ClientBundle/

Contains services for public website.

* Structure:
  ```sh
    Controller/
        Personal/
            DashboardController.php
            ...
        Business/
            DashboardController.php
        BaseController.php
        LandingController.php
        JobController.php
        ...
    Resources/
        views/
            Personal/
                Dashboard/
                    jobsCenter/
                        index.html.twig
                        ...
                ...
            Business/
                Dashboard/
                    jobsCenter/
                        index.html.twig
                        ...
            Landing/
                index.html.twig
            ...
  ```

### /src/Ntech/AdminBundle/

Contains services for admin website.

* Structure:
  ```sh
    Controller/
        DashboardController.php
        AccountController.php
        ActivityController.php
        ...
    Resources/
        views/
            ...
  ```

### /src/Ntech/UploadBundle/

Contains file upload services.

* Structure:
  ```sh
    Controller/
        DownloadController.php
        UploadController.php
        ...
    Uploader/
        UploadFiles.php
        UploadProcessor.php
        ...
  ```

### /src/Ntech/ApiBundle/

Contains services for mobile applications.

* Structure:
  ```sh
    Controller/
        ApiController.php
        PaymentController.php
        PaymentAppleController.php
        ...
    DataPager/
        Cursor.php
        ...
    EventListener/
        ApiExceptionSubscriber.php
        JsonRequestNormalizer.php
    Exception/
        ApiProblemException.php
    Factory/
        ApiResponseFactory.php
    Serializer/
        PropsTransformerNormalizer.php
        ...
    ...
  ```

<!-- WEBSITE OVERVIEW -->
## Website Overview

<div align="center">
  <h3 align="center">Grid configurator: vertical grid</h3>
</div>

<a href="img/2.png?raw=true">
  <p align="center">
    <img src="img/2.png" width="35%">
  </p>
</a>

<div align="center">
  <h3 align="center">Library builder main page</h3>
</div>

<a href="img/3.png?raw=true">
  <p align="center">
    <img src="img/3.png" width="35%">
  </p>
</a>

<div align="center">
  <h3 align="center">Tests suite page</h3>
</div>

<a href="img/4.png?raw=true">
  <p align="center">
    <img src="img/4.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/5.jpg?raw=true">
  <p align="center">
    <img src="img/5.jpg" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/6.png?raw=true">
  <p align="center">
    <img src="img/6.png" width="35%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/7.png?raw=true">
  <p align="center">
    <img src="img/7.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/8.png?raw=true">
  <p align="center">
    <img src="img/8.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/9.png?raw=true">
  <p align="center">
    <img src="img/9.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/10.png?raw=true">
  <p align="center">
    <img src="img/10.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/11.png?raw=true">
  <p align="center">
    <img src="img/11.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/12.png?raw=true">
  <p align="center">
    <img src="img/12.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/13.png?raw=true">
  <p align="center">
    <img src="img/13.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/14.png?raw=true">
  <p align="center">
    <img src="img/14.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/15.png?raw=true">
  <p align="center">
    <img src="img/15.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/16.png?raw=true">
  <p align="center">
    <img src="img/16.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/17.png?raw=true">
  <p align="center">
    <img src="img/17.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/18.png?raw=true">
  <p align="center">
    <img src="img/18.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/19.jpg?raw=true">
  <p align="center">
    <img src="img/19.jpg" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/20.png?raw=true">
  <p align="center">
    <img src="img/20.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/21.jpg?raw=true">
  <p align="center">
    <img src="img/21.jpg" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/22.jpg?raw=true">
  <p align="center">
    <img src="img/22.jpg" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/23.png?raw=true">
  <p align="center">
    <img src="img/23.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/24.png?raw=true">
  <p align="center">
    <img src="img/24.png" width="50%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/25.jpg?raw=true">
  <p align="center">
    <img src="img/25.jpg" width="35%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/26.jpg?raw=true">
  <p align="center">
    <img src="img/26.jpg" width="35%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/27.png?raw=true">
  <p align="center">
    <img src="img/27.png" width="35%">
  </p>
</a>

<div align="center">
    <h3 align="center">Website with documentation</h3>
</div>

<a href="img/28.jpg?raw=true">
  <p align="center">
    <img src="img/28.jpg" width="35%">
  </p>
</a>

<p align="right">(<a href="#top">back to top</a>)</p>