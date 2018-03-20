# Events

- [List of Events](#list-of-events)
- [Disabling Events](#disabling-events)

Cortex emits events on every action. All events are under namespace ```\LaravelCortex\Cortex\Events```.

<a name="list-of-events"></a>
## List of Events

Here is a list of events and their properties that you can listen to:

<table width="100%">
  <thead>
    <tr>
      <th>Event</th>
      <th>Properties</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>CreatingFolder</td>
      <td>
        <ul>
          <li><code>$path</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>CreatedFolder</td>
      <td>
        <ul>
          <li><code>$path</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Cropping</td>
      <td>
        <ul>
          <li><code>$source</code></li>
          <li><code>$destination</code></li>
          <li><code>$x</code></li>
          <li><code>$y</code></li>
          <li><code>$width</code></li>
          <li><code>$height</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Cropped</td>
      <td>
        <ul>
          <li><code>$source</code></li>
          <li><code>$destination</code></li>
          <li><code>$x</code></li>
          <li><code>$y</code></li>
          <li><code>$width</code></li>
          <li><code>$height</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Deleting</td>
      <td>
        <ul>
          <li><code>$path</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Deleted</td>
      <td>
        <ul>
          <li><code>$path</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Moving</td>
      <td>
        <ul>
          <li><code>$source</code></li>
          <li><code>$destination</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Moved</td>
      <td>
        <ul>
          <li><code>$source</code></li>
          <li><code>$destination</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Renaming</td>
      <td>
        <ul>
          <li><code>$source</code></li>
          <li><code>$destination</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Renamed</td>
      <td>
        <ul>
          <li><code>$source</code></li>
          <li><code>$destination</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>UploadingFile</td>
      <td>
        <ul>
          <li><code>$path</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>UploadedFile</td>
      <td>
        <ul>
          <li><code>$path</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>ListingFiles</td>
      <td>
        <ul>
          <li><code>$path</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>ListingDirectoryTree</td>
      <td>
        <ul>
          <li><code>$path</code></li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

<a name="disabling-events"></a>
## Disabling Events

To completely disable emitting events, change your cortex.php configuration file like this:

```php
'events' => false,
```