# 🎓 MFE change steps

Following are steps to change code for header mfe(bgsm-redwood-frontend-component-header) for "bgsm-redwood-frontend-app-authoring" . 💳

## 🚀 Steps

Follow these steps to integrate Razorpay into Open edX:

## Following are steps to change code for header:

1. **Inside mfe that you want to change:**
   ```bash
   npm list
   ```
   **Example:**
   ```bash
   @edx/frontend-component-footer@13.0.4
   @edx/frontend-component-header@5.1.0
   @edx/frontend-enterprise-hotjar@2.0.0
   ```
   **Header is coming from 5.1.0 version of bgsm-redwood-frontend-component-header**

2. **Now from that branch create a new branch in gitlab** 

3. **Retrieve updates from remote repo**
   ```bash
   npm fetch
   ```
   
4. **Change the branch**
   ```bash
   npm checkout new_branch
   ```

   # *Now apply all the changes in mfe*

    
5. **Now fetch code from that branch**:
   ```bash
   git fetch
   ```
   
6. **Install Node-modules**:
   ```bash
   npm i
   npm run build
   git add -f dist
   ```

   *Now add, commit and push changes*
   

7. **Modify `ecommerce/ecommerce/settings/_oscar.py`**:
   ```python
     hooks.Filters.ENV_PATCHES.add_item(
    (
        "mfe-dockerfile-post-npm-install-course-authoring",
        """
         RUN npm install '@edx/frontend-component-header@git+https://PanIIT:gldt-eVQsMKHCFoejCxqjNoNy@gitlab.com/bgsm/bgsm-redwood-frontend-component-header#BGSM-FrontEnd-App-Authoring-Header' --force
         """
    )
   )
   ```
   #### Explanation:
    1. @edx/frontend-component-header@git+https:// *is copy-paste* 
    2. PanIIT:gldt-eVQsMKHCFoejCxqjNoNy &is access token* 
    3. @gitlab.com/bgsm/bgsm-redwood-frontend-component-header *is link for gitlab project* 
    4. #BGSM-FrontEnd-App-Authoring-Header *after # is name of branch*   

8. **tutor config save and build**

9. **After build > tutor local start -d (To recreate the container)**
