

## Termius-cracked Pro MacOS

### Notice

【Software】Termius

【Version】v9.1.1

【Update Date】2024/07/25

【Author】Jimmy

### Usage

- 1. Install package asar (to unzip like tar.gz)

```npm install -g asar```

- 2. Decompress app.asar

```
cd /Applications/Termius.app/Contents/Resources/
asar extract app.asar ./app 
mv app.asar app.asar.bak
rm app-update.yml
```

- 3. Edit and append this code into file app/background-process/assets/main-1ce5c47f.js
Replace: `const e=await this.api.bulkAccount(); -> var e=await this.api.bulkAccount();`

```
var e=await this.api.bulkAccount();
e.account.pro_mode=true;
e.account.need_to_update_subscription=false;
e.account.current_period={
    "from": "2022-01-01T00:00:00",
    "until": "2099-01-01T00:00:00"
};
e.account.plan_type="Premium";
e.account.user_type="Premium";
e.student=null;
e.trial=null;
e.account.authorized_features.show_trial_section=false;
e.account.authorized_features.show_subscription_section=true;
e.account.authorized_features.show_github_account_section=false;
e.account.expired_screen_type=null;
e.personal_subscription={
    "now": new Date().toISOString().slice(0, -5),
    "status": "SUCCESS",
    "platform": "stripe",
    "current_period": {
        "from": "2022-01-01T00:00:00",
        "until": "2099-01-01T00:00:00"
    },
    "revokable": true,
    "refunded": false,
    "cancelable": true,
    "reactivatable": false,
    "currency": "usd",
    "created_at": "2022-01-01T00:00:00",
    "updated_at": new Date().toISOString().slice(0, -5),
    "valid_until": "2099-01-01T00:00:00",
    "auto_renew": true,
    "price": 12.0,
    "verbose_plan_name": "Termius Pro Monthly",
    "plan_type": "SINGLE",
    "is_expired": false
};
e.access_objects=[{
    "period": {
        "start": "2022-01-01T00:00:00",
        "end": "2099-01-01T00:00:00"
    },
    "title": "Pro"
}]
return await this.setUserProfile(e), e;
```

- 4. Logout your Termius account and restart app!

##### Happy coding 🙃🙃