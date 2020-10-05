# Template for CodeRefinery workshop webpages

This repository is a template to set up webpages for CodeRefinery workshops.

To use it, follow these instructions:
- Click the green "Use this template" button.
- Select owner of the new repository and repository name. The name should be
  "year-month-date-place", e.g. "2019-10-16-stockholm".
- Click "Create repository from template"
- You will now be redirected to the new repository.

Adjust these files:
- `title.md`
- `left-column.md`
- `right-column.md`

### Schedule planning

**Host:** Manage zoom meeting, breakout rooms, timekeeping and breaks,
zoom chat, general attendee communication.  **Hackmd:** watches
hackmd, answers questions, organizes it, brings questions up in main
lecture.  **Expert helpers:** Reserve instructors who can help with
difficult problems, especially configuration problems at the very
beginning of each day.  Optional.  **Helper:** breakout room helper, listed at
end (not per day) since they are usually expected to be a helper every
day. **(name)** in parentheses: "I offer to do it
but I am happy if someone replaces me here."

Overlapping roles are allowed when you think it's reasonable!


<table>
<tr>
  <th>Day</th>
         <th>Topics+Instructors</th>
         <th>Host</th>
         <th>Hackmd</th>
         <th>Experts helpers</th>
</tr>
<tr>
  <th>15.oct (Th) 13-14 CEST</th>
         <td>
		     Installation help
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td>Enrico</td><!--expert helpers-->
</tr>
<tr>
  <th>16.oct (F) 13-14 CEST</th>
         <td>
		     Installation help
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td>Enrico</td><!--expert helpers-->
</tr>
<tr>
  <th>20.oct (T)</th>
         <td>
		     intro: TBA<br>
		     git-intro: TBA<br>
		     git-intro: TBA<br>
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td>Enrico</td><!--expert helpers-->
</tr>
<tr>
  <th>21.oct (W)</th>
         <td>
		     git-intro: TBA<br>
		     git-intro: TBA<br>
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td>Enrico</td><!--expert helpers-->
</tr>
<tr>
  <th>22.oct (Th)</th>
         <td>
		     git-collab: TBA<br>
		     git-colalb: TBA<br>
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td>Enrico</td><!--expert helpers-->
</tr>
<tr>
  <th>27.oct (T)</th>
         <td>
		     intro: TBA<br>
		     rep research: TBA<br>
		     social coding: TBA<br>
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td></td><!--expert helpers-->
</tr>
<tr>
  <th>28.oct (W)</th>
         <td>
		     documentation: TBA<br>
		     jupyter: TBA<br>
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td>Enrico (maybe)</td><!--expert helpers-->
</tr>
<tr>
  <th>29.oct (Th)</th>
         <td>
		     testing: TBA<br>
		     modular code: TBA<br>
		     outro: TBA<br>
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td>Enrico (maybe)</td><!--expert helpers-->
</tr>
</table>

Expert helpers:
- Enrico Glerean
- TBA
- TBA



### Changing the status of the registration button

Registration is not yet open:
```html
<a class="btn btn-info disabled" href="#" data-mode="1" target="_blank">Registration will open soon</a>
```

Registration is open (adjust the `href`):
```html
<a class="btn btn-success" href="#" data-mode="1" target="_blank">Register here</a>
```

Registration is closed:
```html
<a class="btn btn-danger disabled" href="#" data-mode="1" target="_blank">Registration is closed</a>
```
